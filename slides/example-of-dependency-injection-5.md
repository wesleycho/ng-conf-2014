##  Example of Dependency Injection

### main()

	import {Injector} from 'di/annotations';
	import {CoffeeMaker} from './coffeeMaker';

	function main() {
		var injector = new Injector;
		var coffeeMaker = injector.get(CoffeeMaker);

		coffeeMaker.brew();
	}

	main();