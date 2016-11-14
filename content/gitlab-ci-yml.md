## Configurations: gitlab-ci.yml

----------

### Let's start building the app

- What is the `gitlab-ci.yml` file?
- Review the file with CI Lint at Pipelines
- Our plan:
  - Image
  - Services
  - Environments
  - Stages  
  - Jobs
----------
  - Before and After Scripts
  - Caching
  - Artifacts & On Success
  - Only and except
  - When
  - Pages

----------

### Docker Image & Registry

Use a public image:
```
image: ruby:2.3
```
Use a custom image:
```
image: "registry.gitlab.com/gitlab-org/ci-training-sample:ruby-and-gems"
```

----------

### Services and Variables

- Pre defined vars: https://docs.gitlab.com/ce/ci/variables/README.html

```
services:
  - postgres

variables:
  POSTGRES_DB: rails-sample-1_test
  POSTGRES_USER: root
  POSTGRES_PASSWORD: ""
```
----------

### Stages

- Default stages: build, test, deploy
- User can define any custom stage and any number of jobs per stage

```
stages:
- build
- test
- deploy
```
----------

### Before and After Scripts

```
before_script:
  - echo CI_BUILD_STAGE
  - apt-get update
  - apt-get install nodejs -y
  - gem install bundler --no-ri --no-rdoc
  - bundle install
```
----------

### Caching

```
cache:
  key: "%CI_BUILD_STAGE%/%CI_BUILD_REF_NAME%"
  paths:
  - vendor/ruby
```

----------

### Templates
- Anchors, aliases and merging with yml

```
.hidden_anchor: &ruby_info
  script:
  - echo ruby -v
  - echo which ruby

env_info:
  <<: *ruby_info
  stage: build
```

----------

### Artifacts & On Success

```
system_specs:
  stage: build
  script:
  - echo "author:"
  - echo GITLAB_USER_EMAIL
  - touch system_info
  - uname -a > system_info
  artifacts:
    when: on_success
    paths:
    - system_info
```

----------

### Tests and Manual trigger

```
rspec:
  stage: test
  when: manual
  script:
  - "sed -i 's/host:.*/host: postgres/g' config/database.yml"
  - "sed -i 's/username:.*/username: root/g' config/database.yml"
  - bundle exec rake db:migrate RAILS_ENV=test
  - bundle exec rake spec
```

----------

### Environments, Only and Deploying

```
pseudo-deploy:
  stage: deploy
  script:
  - echo "Deploying ... not really"
  only:
  - production
  environment:
    name: production
```

----------

### Pages

```
pages:
  stage: deploy
  script:
  - echo 'Publishing pages'
  artifacts:
    paths:
    - public
  only:
  - master
```
