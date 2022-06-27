# springBoot1.0
This repository is for using all common Annotations

	1. Bean getters and setters / constructors

	@SpringBootApplication(scanBasePackages={"com.reachrk.microservices.limitsservice"})
	public class LimitsServiceApplication {
		public static void main(String[] args) {
			SpringApplication.run(LimitsServiceApplication.class, args);
		}
	}

	2. Bean getters and setters /constructors
	public class Limits {
		private int minimum;
		private int maximum;

	3. Bean Getters and setters
	
	@ConfigurationProperties("limits-service")
	@Component
	public class Configuration {
		private int minimum;
		private int maximum;
	
	4. Controller to handle /limits request
	@RestController
	public class LimitsController {
		
		@Autowired
		private Configuration configuration;
		
		@GetMapping("/limits")
		public Limits retrieveLimits() {
			return new Limits(configuration.getMinimum(),configuration.getMaximum());
		}
	}
	
	5. Application.properties
	
	spring.config.import=optional:configserver:http://localhost:8888
	limits-service.minimum=3
	limits-service.maximum=997
	
Output :
		
![image](https://user-images.githubusercontent.com/8842789/175930900-735a8e94-356c-4b74-a5e8-aeb8a645d430.png)
