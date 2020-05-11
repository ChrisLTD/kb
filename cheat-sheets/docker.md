# Docker

Start with a Docker Compose file:`docker-compose up`

Start with a Docker Compose file and run as a background daemon:`docker-compose up -d`

Force recreate & rebuild a Docker Compose containers:`docker-compose up --force-recreate --build`

Stop services with Docker Compose:`docker-compose stop`

Stop and remove services with Docker Compose:`docker-compose down`

Connect to container shell:`docker exec -it CONTAINER_NAME_HERE bash`

Build Docker Compose project:`docker-compose build`

Stop containers and removes volumes:`docker-compose down -v`

See Docker processes:`docker ps`

See Docker stats \(CPU, Memory, Network\):`docker stats`

View Docker Compose logs:`docker-compose logs`

Remove unused images:`docker image prune`

Remove stopped containers:`docker container prune`

Remove unused volumes:`docker volume prune`

Remove unused networks:`docker network prune`

Run all prunes:`docker system prune`

See all containers \(even stopped containers\):`docker ps -a --no-trunc`

Remove containers that haven't been used in weeks:`docker ps -a | grep Exited | grep "weeks ago" | awk '{print $1}' | xargs docker rm`

Remove container:`docker rm CONTAINER_NAME`

Remove image:`docker rmi IMAGE_NAME`

## Documentation links:

* [Official documentation](https://docs.docker.com)
* [Docker Tips and Cheatsheet](https://blog.jez.io/2015/07/12/docker-tips-and-cheatsheet/)
* [Local WordPress dev with Docker](https://medium.com/@tatemz/local-wordpress-development-with-docker-3-easy-steps-a7c375366b9)
* [Persisting MySQL data with Docker](https://stackoverflow.com/questions/39175194/docker-compose-persistent-data-mysql/39208187#39208187)

