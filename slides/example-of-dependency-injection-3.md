##  Example of Dependency Injection

### Much Better

	function main() {
		var injector = new Injector(...);
		var coffeemaker = injector.get(CoffeeMaker);

		coffeemaker.brew();
	}

	CoffeeMaker.$inject = ['grinder', 'pump', 'heater'];
	function CoffeeMaker(grinder, pump, heater) {
		...
	}

	main();