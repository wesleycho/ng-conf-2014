##  Example of Dependency Injection

### A Little Better

	function main() {
		var electrity = new Electricity();
		var heater = new Heater(electricity);
		var grinder = new Grinder(electricity);
		var pump = new Pump(electricity);
	    var coffeemaker = new CoffeeMaker(grinder, heater, pump);
	    coffeemaker.brew();
	}

	main();