# Site Deploys

## Bitbucket

Go into the Repo settings / Pipelines / SSH Keys Add your destination server\(s\) to Known hosts 

Add `USER` and `PASSWORD` variables \(if you're not using an SSH key\) to the Repository variables

Add a `bitbucket-pipelines.yml` file. Here's a basic one for deploying to a SFTP server:

```text
image: atlassian/default-image:2

pipelines:
  default:
    - step:
        name: 'Deployment to Staging'
        deployment: staging
        script:
          - echo "Your deployment to staging script goes here..."
    - step:
        name: 'Deployment to Production'
        deployment: production
        trigger: 'manual'
        script:
          - pipe: atlassian/sftp-deploy:0.5.7
            variables:
              USER: $USER
              PASSWORD: $PASSWORD
              SERVER: 'remoteserver.com'
              REMOTE_PATH: '/htdocs/wp-content/themes/mytheme'
              LOCAL_PATH: 'wp-content/themes/mytheme/*'
```

## Github Actions

## Dandelion

[https://github.com/scttnlsn/dandelion](https://github.com/scttnlsn/dandelion)

