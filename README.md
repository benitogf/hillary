# hillary

Remote execution tool, ssh conection following a YML config file.

## Requirements

https://github.com/quartzjer/ursa/#windows-install

## Installation

```
npm i -g hillary
```

## Config

Create a file ```hillary.yml``` with the following structure:

```
deploy_before:
  - git status
  - git checkout .
  - git pull
deploy_after:
  - git status
ssh:
    cwd: /var/www/hillary
envs:
  dev:
    deploy:
      - npm run build:dev
    host: XX.XXX.XX.XXX
    username: hillary
    privateKey: path/to/key.txt
  stage:
    deploy:
      - npm run build:stage
    host: WW.WWW.WW.WWW
    username: hillary
    privateKey: path/to/key.txt
  prod:
    deploy:
      - npm run build:prod
    host: OO.OOO.OO.OOO
    username: hillary
    privateKey: path/to/key.txt
```

Then run in a the directory that contains the file

```
hillary dev
```
```
hillary stage
```
```
hillary prod
```
