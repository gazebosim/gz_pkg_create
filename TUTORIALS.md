# Commands

To get list of possible arguments run- ```ign pkg_create -h```

<p align="center">
<img src="https://user-images.githubusercontent.com/78502324/187427160-dc115052-6823-47f3-88f8-b2b0d69e6fda.png" width="900" >
</p>

Based on requirement select arguments, an example command is-

```ign pkg_create -n test_package --init-with-example-system  -b ament_cmake -e colcon --ign_dependecies```

# Arguments

Currently supported arguments are-

1. **Name**- Name of new package.
2. **Init-with-example-system**- Selecting this will add example world,model,plugin and executbale to the package.Also code for installing and sourcing will be also added using following [macros](https://github.com/gazebosim/gz-cmake/pull/262).You can checkout comments for detailed description of macros.
3. **Built_type** [Default- cmake]- Currently subcommand support ament and cmake package types. Tn ament_cmake type, various ament dependencies and macros will be added to CMakeLists.txt
4. **Export_type** [Default - colcon]- Currently subcommand supports colcon and plain cmake export types.In colocn pkg mode it will create colocon.pkg and hooks whereas in plain-cmake it will create a .sh file for exporting required variables.
5. **Ign_dependecies**- This argument will dependencies on common gazebo packages.
6. **Gazebo_version** [Default- Fortress]- Specify the version of gazebo which you want dependeices for.

# Testing

To test the package first install it and then run follwing commands-

```
$ mkdir test_ws
$ cd test_ws
$ mkdir src
$ cd src
$ ign pkg_create -n test_package --init-with-example-system  -e colcon --ign_dependecies
$ cd ..
$ colcon build --merge-install
$ source install/setup.bash
````

You can try executable demo by running-
```
random_points
```
You will see 2 random points being generated. You can try world and plugin demo by running-

```
ign gazebo empty_platform_with_elevator.sdf -v4
```
You will see example world whose path has been exported run. Also on the terminal you will hello world plugin giving information about state of simulation.


