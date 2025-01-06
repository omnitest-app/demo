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

### Motivation

1. **User value**: A testing plan that is a synthesis of features, test cases and implementation focuses all efforts naturally towards user value.
2. **Freedom to refactor**: The automatically generated change-based test plan improves product team's ability to modify the codebase safely. Easier and cheaper maintenace leads to more effective feature development.
3. **Faster feedback loops**: Waiting is reduced in multiple ways, because a near instant automatic analysis can be run at will, by those who need it, at any stage of development. 

#### Benefit calculations

**Test plan creation**

In a pilot case, a comparable testing plan to an 8 hour effort over 3 days using a wiki-like system was achieved with Omnitest in minutes.

Simplified, assuming such a workload on 
- a monthly basis: 12*8h = 96h/year
- a weekly basis: 52*8h = 416h/year

with an hourly cost between 30€ to 100€, using Omnitest could reduce costs by
- 2880€ to 12480€ for 30€/h cost
- 9600€ to 41600€ for 100€/h cost


**Efficiency and effectiveness benefits**

Simplified, assuming a continuous long-term productivity increase month-to-month of
- 1% per person
- 10% per person

would [compound](https://en.wikipedia.org/wiki/Compound_interest#Periodic_compounding) over
- 1 year: between 13% and 214%
- 3 years: between 43% and 2991%

into theoretically produced extra value based on yearly cost of
- 50 000€: between `13%/100% * 50 000€ = 6500€` and `2991% / 100% * 50 000€ = 1 495 500€`
- 200 000€: between `13%/100% * 200 000€ = 26 000€` and `2991% / 100% * 50 000€ = 5 982 000€`

## User Guide

### Requirements
- a local git repository
- ability to manage changes, e.g. by using Github Desktop
- a project built using supported languages and frameworks (JSX/TSX, VueJS, Flutter)


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
Excluding folders
```
  "config": {
    "excludes": ["**/resources/templates/**"]
  }
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
