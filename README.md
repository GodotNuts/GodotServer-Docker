# GodotServer-Docker

A repo with everything needed to spin up a Godot Server in Docker using Alpine Linux

## :coffee: Contributors

- [Chuck Lindblom](https://github.com/BearDooks) (Creator)


## :arrow_down:  Cloning
SSH:
```bash
git clone git@github.com:GodotNuts/GodotServer-Docker.git
```

HTTPS:
```
git clone https://github.com/GodotNuts/GodotServer-Docker.git
```

## :question: How to Use

1. Clone the repository to your docker server
2. Edit the file `docker-compose.yaml` with the correct information
    1. Change the ports to the correct values
3. Edit the `dockerfile` to have the correct information for the server to download and run the Godot Application
4. Run the docker container with the command `docker-compose up -d`

## :bug: Reporting an Issue

Please make sure to open a bug report if you have any questions. The more detail in there the better

## :computer: Making Contributions

Contributions are always welcome. Please feel free to fork this repo and request changes

## :memo:  License

This plugin falls under the [MIT License](https://github.com/GodotNuts/GodotServer-Docker/blob/main/LICENSE)

