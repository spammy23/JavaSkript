# JavaSkript

## Introduction

> JavaSkript provides a simple way for you to access the Bukkit api through JavaScript

## Usage

First you must register your plugin, the `pluginManager.register` method works like a plugin.yml, here your plugin's name, commands, description, and many other variables declared in the plugin.yml of a regular plugin. the `plugin` variable is an instance of your JS plugin.
```javascript
pluginManager.register({
    name: "Test plugin",
    description: "Example plugin",
    version: 1.0,
    commands: {
        test: {
            usage: "/test"
        }
    },
    authors: ["spammy23"]
}, plugin);
```
All code including the bukkit API is in the single variable `bukkit`, it's usually easier to use `with(bukkit)`.
To register a command, you use the `pluginManager.registerCommand` method which takes 6/7 arguments.  The first being your `plugin` instance, the second being the name of the command, the third being description, fifth being the usage, the sixth being the function that executes the command and the optional seventh being an array of aliases.
`pluginManager.registerCommand(plugin, name, description, usage, commandFunction/*, aliases*/)`
```javascript
with(bukkit) {
    pluginManager.registerCommand(plugin, "test", "An example command", "/test",
        function(sender, command, args){ //optional alias argument
            sender.sendMessage("I have received your command: " + command.getName())
            return true
    }, ["alias1", "alias2"]) // The array of aliases is optional
}
```
While registering events, you use the`pluginManager.registerEvent` method, this takes two variables, the first being the handler and the second being the class for the event you are listeneing to 
```javascript
with(bukkit) {
    pluginManager.registerEvent(
        function(event){
            print("command: "+event.getCommand());
            print("Test successful , received command");
        }, ServerCommandEvent);
}
```

## Installation

> To install, place the JavaSkript.jar archive in your plugins folder and insert your JS plugins in the plugins/JavaSkript folder created on the first run
