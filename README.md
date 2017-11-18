"# module.js" 

How to use (easy!):
1) Register all modules once each with module.register(identification, pathToModuleFromHtmlFile).
	Consider creating a seperate .js file to register all of the modules, with a constant to identify each one.
2) Call module.loadModules(callback) and run all code that needs the modules inside the callback.
	If modules have already been previously loaded, they will not be loaded again (callback may be called immediately).
3) Inside the callback, get each module with module.use(identification).
	Do not attempt to use module.use outside of the module.loadModules callback, because perhaps the modules have not been loaded yet! (An error will be thrown in such a case.)

Creating a module:
1) Each module is a seperate .js file which is not linked to from the HTML (the library adds the <script> tags for you when necessary)
2) Your module's code will be run at most once, and the user of module.use(identification) will be given the value exported in your module
3) Your module exports its value by setting window.exports to the desired return value
	Consider returning an object, which will have properties and methods for the caller to use.
	Consider creating this object inside a closure, so as not to pollute the global namespace, while providing a private interface for your object.