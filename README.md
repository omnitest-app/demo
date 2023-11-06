*NOTE: Under construction*

# Omnitest Demonstrations
Guides to using Omnitest in various software development workflows.


**Flagship use case**: 
`omnitest . --runner=jest --pull-request`


TODO: Link to webshop.


## Omnitest CI
The CLI for filtering tests based on changes in the code.

### How-to

#### Overview
1. Get Omnitest CI binary and a license
2. Make it executable on your platform in your preferred way
3. Make a change in your code
4. Run Omnitest and give a path to your repository
5. Grab the list of tests Omnitest reported
6. Execute the list of tests

#### Specific: NodeJS variations
1. Install a NodeJS dependency `npm -g install madge` ([https://github.com/pahen/madge#installation](link))
2. Change a line of code
3. Execute `omnitest path/to/repo`
4. Execute tests, e.g. `npm exec jest --testsByPath <list of tests from Omnitest>`

**Demo: ExpressJS + Jest**
```
# Clone a starter (e.g. https://github.com/w3cj/express-api-starter-ts)
npx create-express-api --typescript --directory demo
cd demo

npm install
npm -g install madge

# Change something
echo "// a demonstration" > src/interfaces/MessageResponse.ts

# Analyse and run tests
omnitest . --runner=jest
```

#### Specific: GitHub pull request workflow

```
- uses: actions/checkout@v4
  with:
    fetch-depth: 0 # It's important to fetch enough of the history to be able to git diff branches

- name: Run tests with Omnitest filtering
  run: |
    export OMNITEST_CI_KEY=${{ vars.OMNITEST_LICENSE }}
    omnitest --runner=jest --pull-request
```

#### Built-ins

##### NodeJs

- File dependencies: with 3rd party dependency `madge`
- Jest test execution: `npm exec jest` with `npm` as the package manager and `jest` as a project dependency
- Default test automation filename matching glob: `*test*.*`
  
TODO
- Support pnpm, yarn, and bun as well


##### Other languages / stacks

Omnitest supports providing data manually through
- changes.json
- dependencies.json
- tests.json
Read "Providing data manually" for more.

- Default test automation filename matching glob: `*test*.*`
- TODO: Manually provide a test automation filename matching glob `--ta "*spec*.rb"`

  
#### Change management

##### Providing changes manually
It is possible to provide changes manually via a `changes.json` located at the root of the provided project directory. If the file exists, it will be the sole source of changes, unless the `--pull-request` was provided, in which case the file will be skipped.

Changes.json format
```
[
  { "target": "path/to/changed/file" }
]
```

These changes will be used just like auto-discovered changes.
```
./your-script-to-create-changes > changes.json
omnitest . --runner=jest
```

You can also further process the effects of the changes manually.
```
./your-script-to-create-changes > changes.json
declare -a affected_tests=$(omnitest . --names-only)

# Read the changes in your script line by line,
echo ${affected_tests} | ./your-script-to-run-affected-tests

# or do some data formatting.
#   E.g. Replace \n's and provide the test files as arguments.
```

##### Changes from pull requests in GitHub
When `--pull-request` is provided, Omnitest will automatically compare the target and source branches for differences. For this, the `GITHUB_BASE_REF` and `GITHUB_SOURCE_REF` need to be provided. They define the target and source branches as defined in [GitHub Variables](https://docs.github.com/en/actions/learn-github-actions/variables).

Note: The further apart the source and target branches are, the more differences will be found. For the quickest test runs the pull request source branch should be up to date with the target. This way only the proposed new changes will be considered as differences. This is where rebasing and merging target->source first come in as some useful tools.

#### Providing data manually

Changes.json format
```
[
  { "target": "path/to/changed/file" }
]
```
Dependencies.json format
```
[
  { "source": "path/to/file/A" },
  { "target": "path/to/file/B" }
]
```
Tests.json format
```
[
  { "file": "path/to/test/file" }
]
```


#### Get Omnitest CI binary and license
TODO
- where and how
- subscriptions & billing

#### License usage
An environment variable is required:
`export OMNITEST_CI_KEY=a-valid-license-key`

#### Platforms
Runs on
- Ubuntu (Built on GitHub's ubuntu-20.04 runner)

Dependencies outside of GitHub's runners
- Ubuntu: libssl-dev


Clever usage of the workflow outside of the GitHub may be possible.
