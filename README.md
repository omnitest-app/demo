# Omnitest: Exciting, safe and effective releases
An automatic software testing planner for developers, testers and product managers. 

[Download app](https://web.crabnebula.cloud/omnitest/omnitest/releases)

## Working with Omnitest
- Improves product teams' innovation ability 🧠
- Protects customer value 🤝
- Decreases maintenance costs 💸

through
- Proactively mapping customer value to code using a test plan
- Providing instant and continuous feedback in development, testing and project planning phases
- Reducing surprises and effort in dealing with effects of new code changes to existing features

by 
- Automatically extracting coded features into a test plan
- Automatically shrinking test sets to the minimum required to cover code changes
- Automatically adjusting to existing architecture based on file dependencies


It is a desktop app that works on individual users' machines, using locally available git repositories. 



### Requirements
- a local git repository
- ability to manage changes, e.g. by using Github Desktop
- a project built using supported languages and frameworks (JSX/TSX, VueJS, Flutter)

### Motivation

1. User value: A testing plan that is a synthesis of features, test cases and implementation focuses all efforts naturally towards user value.
2. Freedom to refactor: The automatically generated change-based test plan improves product team's ability to modify the codebase safely. Easier and cheaper maintenace leads to more effective feature development.
3. Omnitest is fast: Waiting is reduced in multiple ways, because a near instant automatic analysis can be run at will, by those who need it, at any stage of development. 

**Benefit calculation**
In a pilot case, a comparable testing plan to an 8 hour effort over 3 days using a wiki-like system was achieved with Omnitest in minutes.

Simplified, assuming such a workload on 
- a monthly basis: 12*8h = 
- a weekly basis: 52*8h = 


## User Guide


### Getting started

1. Open [Omnitest](https://web.crabnebula.cloud/omnitest/omnitest/releases)
2. Open project
3. Review `Testing > Testing Round`
4. Make code changes
5. Reload project
6. Repeat steps 3-6


### Adjusting the plan
1. Open `test.plan.json`
2. Modify 
3. Reload project in Omnitest


#### Features
You can adjust the feature extraction rules in `config.features`.

**Useful examples**
```
  "config": {
    "features": [
      {
        "alias": "All Views",
        "matchers": ["**/views/**", "**/*{View}*.tsx"]
      },
      {
        "alias": "Feature set: Customer Import & Export",
        "matchers": ["**/{import,export}/**/*{View}*.tsx", "**/*{Export,Import}*{View}*.tsx"]
      }
]
```

#### Test automation

You can adjust the test automation extraction rules in `config.test_automation` by setting glob matchers.

**Useful examples**

```
    "test_automation": {
      "file_name_globs": ["*.spec.ts", "*.test.ts"]
    }
```

#### Changes

You can adjust the change extraction rules in `config.changes` following the below examples.

**Useful examples**


- Local vs remote
```
    "changes": {
      "old": "HEAD{upstream}",
      "new": "HEAD"
    }
```

- Current branch vs main branch
```
    "changes": {
      "old": "master",
      "new": "HEAD"
    }
```

- Changes between particular commits: 

Checkout the newer commit and adjust the older commit hash
```
    "changes": {
      "old": "<older git commit hash>",
      "new": "HEAD"
```
