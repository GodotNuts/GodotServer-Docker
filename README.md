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

This system will use a few variables to auto create a docker container and clone a godot game into it. Once done it will automatically start the Godot Server. You need to make sure that the PCK file is in the root of the repo you are cloning or this will not work.

The best way to do this for now is to have a public repo with the PCK file in it

1. Ensure you have a `.PCK` file in a repo ready to clone
2. Clone the repository to your docker server
3. Edit the file `docker-compose.yaml` with the correct information
    1. Change the ports to the correct values
4. Edit the `dockerfile` to have the correct information for the server to download and run the Godot Application
    1. Edit `GODOT_VERSION` to use the correct version of Godot you want
    2. Edit `GODOT_GAME_NAME` to the name of the .PCK file you are using without the .PCK
        1. Ex. `Godot_Game.pck` would be `Godot_Game`
    3. Edit `HTTPS_GIT_REPO` to be the clone command
5. Run the docker container with the command `docker-compose up -d`

## :bug: Reporting an Issue

Please make sure to open a bug report if you have any questions. The more detail in there the better

## :computer: Making Contributions

Contributions are always welcome. Please feel free to fork this repo and request changes

## :memo:  License

This plugin falls under the [MIT License](https://github.com/GodotNuts/GodotServer-Docker/blob/main/LICENSE)

