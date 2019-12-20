---
title: "Confusing CORS Explained"
date: 2018-06-22
categories: 
  - Cross Origin Resource Sharing
  - CORS
---

I have always been confused with the CORS errors and in this post I'll try to share my understanding of CORS for now.

To begin with, the long version of CORS is "Cross-Origin Resource Sharing". It also referred as same origin policy. Let's explain first, what origin is? Origin is defined by 3 parts in a URL, protocol (scheme), host (domain), and port of a URL. For example, for the following URL "http://example.com/doc.html", protocol is http, host is example.com, and port is 80. [1]

Since we know what origin is, let's dive into what is the meaning CORS and how does this term arised. The main intent of this constraint is to make people be able to visit untrusted websites safely. If there would not be such policy the session of the user might be used to reach sensitive information from the trusted websites. Since browsers does not want to allow this, the request that are coming from different origins are not allowed in the browsers. [2]

A very basic image that explains this idea is shown below:

<figure>
    <a href="/assets/images/CORSRequest.png"><img src="/assets/images/CORSRequest.png"></a>
    <figcaption>Image that explains CORS request</figcaption>
</figure>

The Spring page also explains this topic in a very neat way. The same-origin policy is an important security concept implemented by web browsers to prevent Javascript code from making requests against a different origin (e.g., different domain) than the one from which it was served. Although the same-origin policy is effective in preventing resources from different origins, it also prevents legitimate interactions between a server and clients of a known and trusted origin.[3]

To avoid this exception and to be able to reach servers from other origins, spring serves two methods. A coarse grained method which allows for a method or in a whole controller. The second way is to allow request within the whole project. 

**Fine Grained Way: Method or Controller Configuration**

In a controller, a method can be allowed for request from cross origins by adding @CrossOrigin annotation above the method.

```java
@RestController
@RequestMapping("/account")
public class AccountController {

	@CrossOrigin
	@GetMapping("/{id}")
	public Account retrieve(@PathVariable Long id) {
		// ...
	}
}
```

A more general way of fine grained method is to add @CrossOrigin annotation on top of the controller class. In this case all the methods are enabled for CORS support in the controller. In method configuration, only the methods that are annotated with @CrossOrigin are allowed for the requests. 

```java
@CrossOrigin(origins = "http://domain2.com", maxAge = 3600)
@RestController
@RequestMapping("/account")
public class AccountController {

	@GetMapping("/{id}")
	public Account retrieve(@PathVariable Long id) {
		// ...
	}

	@DeleteMapping("/{id}")
	public void remove(@PathVariable Long id) {
		// ...
	}
}
```

**Coarse Grained Way: Global CORS Configuration**
To define a global CORS setting, Spring's WebMvcConfigurerAdapter class is used. That class has be to extended in a configuration class and the addCorsMappings method has to be overriden. 

```java
@Configuration
@EnableWebMvc
public class WebConfig extends WebMvcConfigurerAdapter {

	@Override
	public void addCorsMappings(CorsRegistry registry) {
		registry.addMapping("/**");
	}
}
```

If Spring Boot is used the following way has to be selected for CORS configuration. 

```java
@Configuration
public class MyConfiguration {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurerAdapter() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**");
            }
        };
    }
}
```

To configure CORS settings in UI side, some configurations are also needed. Here I'll give configurations for the AngularJS.


```json
{
  "/api/*": {
    "target": "http://host:port/",
    "secure": false,
    "logLevel": "debug",
    "changeOrigin": true
  }
}
```



package.json
"scripts": {
    "ng": "ng",
    "start": "ng serve  --host 0.0.0.0 --port 1234 --proxy-config proxy.conf.json",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e"
  },


**References**

[1] https://www.w3.org/Security/wiki/Same_Origin_Policy  
[2] https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS  
[3] https://spring.io/understanding/CORS  
[4] https://medium.com/@buddhiv/what-is-cors-or-cross-origin-resource-sharing-eccbfacaaa30  
[5] https://spring.io/blog/2015/06/08/cors-support-in-spring-framework