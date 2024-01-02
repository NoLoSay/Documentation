>demo.controller.ts
```TS
import { Controller } from '@nestjs/common';

@Controller('demo')
export class DemoService {
	constructor(private readonly demoService: DemoService) {}

	@Get()
	async getDemo() {
	  return demoService.returnDemo();
	}
}
```

>demo.controller.spec.ts
```TS
describe('DemoController', () => {
	let controller: DemoController;

	beforeEach(async () => {
		const module: TestingModule = await Test.createTestingModule({
			controllers: [DemoController],
			providers: [DemoService],
		}).compile();

		controller = module.get<DemoController>(DemoController);
	});

	it('should be defined', () => {
		expect(controller).toBeDefined();
	});
});
```