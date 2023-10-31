*NOTE: Under construction*

# Omnitest Demonstrations
Guides to using Omnitest in various software development workflows.


**Flagship use case**: 
`omnitest . --runner=jest --pull-request`




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
4. Execute tests, e.g. `npm test <list of tests from Omnitest>` o

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
TODO
```
- name: Run tests with Omnitest filtering
  run: omnitest --runner=jest --pull-request
```


#### Get Omnitest CI binary and license
TODO
- where and how
- platforms
- subscription & billing

#### Executing
TODO
- where and how
- license usage
- platforms
- built-ins & manual data creation

#### Change management
TODO
- providing a list of changes
