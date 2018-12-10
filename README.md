# Defender
Defender is a lightweight, flexible, and highly available permission framework that fully embraces spring-boot.If we need to make it easier to add permission management to the service on a daily basis, Defender is the Defender!

![](https://user-gold-cdn.xitu.io/2018/12/10/16796c88864925b7?w=871&h=278&f=png&s=13234)

It eliminates the need to repeatedly write custom annotations and facets, and allows you to flexibly specify different patterns of defense networks by simply calling a simple API.

## Quick start
Defender is easy to deploy in two steps, make sure your service USES the spring-boot technology stack before using it, and that you introduce spring-boot-starter aop and spring-boot-starter web modules.
#### Dependency
```
<dependency>
	<groupId>com.smallnico</groupId>
	<artifactId>defender</artifactId>
	<version>##last-version</version>
</dependency>
```
#### Configuration
```
@Configuration
@EnableDefender("* org.nico.trap.controller..*.*(..)")
public class DefenderTestConfig {
	@Bean
	public Defender init(){
		return Defender.getInstance()
				.registry(Guarder.builder(GuarderType.URI)
						.pattern("POST /user")
						.preventer(caller -> {
							return Result.pass();
						}))
				.ready();
	}
}
```
## Advance
 - [中文文档](https://github.com/ainilili/defender/blob/master/DOCUMENT_CN.md)
 - [English Document](https://github.com/ainilili/defender/blob/master/DOCUMENT_EN.md)