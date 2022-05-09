# Site Deploys

## Bitbucket

Go into the Repo settings / Pipelines / SSH Keys Add your destination server(s) to Known hosts&#x20;

Add `USER` and `PASSWORD` variables (if you're not using an SSH key) to the Repository variables

Add a `bitbucket-pipelines.yml` file. Here's a basic one for deploying to a SFTP server:

```
image: atlassian/default-image:2

pipelines:
  default:
    - step:
        name: 'Deploy to Staging'
        script:
          - echo "Your deployment to staging script goes here..."
    - step:
        name: 'Deploy MU-Plugins to Production'
        trigger: 'manual'
        script:
          - pipe: atlassian/sftp-deploy:0.5.7
            variables:
              USER: $USER
              SERVER: 'sftp.pressable.com'
              REMOTE_PATH: '/htdocs/wp-content/mu-plugins'
              LOCAL_PATH: 'wp-content/mu-plugins/*'
              PASSWORD: $PASSWORD
    - step:
        name: 'Deploy Theme to Production'
        trigger: 'manual'
        script:
          - pipe: atlassian/sftp-deploy:0.5.7
            variables:
              USER: $USER
              SERVER: 'sftp.pressable.com'
              REMOTE_PATH: '/htdocs/wp-content/themes/YOUR_THEME'
              LOCAL_PATH: 'wp-content/themes/YOUR_THEME/*'
              PASSWORD: $PASSWORD
```

## Github Actions

## Dandelion

[https://github.com/scttnlsn/dandelion](https://github.com/scttnlsn/dandelion)
