##  Example of Dependency Injection

### Ugliness

	function CoffeeMaker() {
		var electrity = new Electricity();
		var heater = new Heater(electricity);
		var grinder = new Grinder(electricity);
		var pump = new Pump(electricity);
		this.brew = function() {
			grinder.grind();
			heater.on();
			pump.pump();
		};
	}
    var coffeemaker = new CoffeeMaker();
    coffeemaker.brew();