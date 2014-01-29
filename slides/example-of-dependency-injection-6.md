##  Example of Dependency Injection

### Mock Class

	import {Provide} from 'di/annotations';

	import {Heater} from './heater';

	@Provide(Heater)
	class MockHeater {
		on() {
			...
		}
	}

### main()

	import {Injector} from 'di/annotations';
	import {CoffeeMaker} from './coffeeMaker';
	import {MockHeater} from './mockHeater';

	function main() {
		var injector = new Injector([MockHeater]);
		var coffeeMaker = injector.get(CoffeeMaker);

		coffeeMaker.brew();
	}

	main();