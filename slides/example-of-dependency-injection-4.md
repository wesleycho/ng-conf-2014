##  Example of Dependency Injection

### New implementation

	import {Inject} from 'di/annotations';

	import {Heater} from './heater';
	import {Grinder} from './grinder';
	import {Pump} from './pump';

	@inject(Grinder, Pump, Heater)
	export class CoffeeMaker {
		constructor(grinder, pump, heater) {
			...
		}

		brew() {
			console.log('Brewing a coffee');
		}
	}
	// or if annotations don't come in ES6
	// CoffeeMaker.annotations = [
	//   new Inject(Grinder, Pump, Heater);
	// ];