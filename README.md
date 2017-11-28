# Camel Springboot Test Utils
[![Build Status](https://travis-ci.org/toolisticon/camel-spring-boot-testutils.svg?branch=master)](https://travis-ci.org/toolisticon/camel-spring-boot-testutils.svg?branch=master)

This projects supplies a small library making testing of Apache Camel components. 

## Features

### Test rule

There is a lot written about Camel Spring Testing, but all approaches are based on inheritance 
or using a special runner. If this is not an option fo you, you may use the test rule for this:

    ...
    import org.springframework.test.context.junit4.rules.CamelSpringClassRule;
    import org.springframework.test.context.junit4.rules.SpringMethodRule;
  
  
    @SpringBootTest
    public class SimpleRuleTest {
    
        @ClassRule
        public static final CamelSpringClassRule springClassRule = new CamelSpringClassRule();
    
        @Rule
        public final SpringMethodRule springMethodRule = new SpringMethodRule();
  
        @Autowired
        private CamelContext camelContext;
    
        @Test
        @DirtiesContext
        public void testMe() throws Exception {
          // do something with camelContext here
        }
    } 
      
### ExcludeRoutes

There is a standard annotation to exclude routes `org.apache.camel.test.spring.ExcludeRoutes`. This is not 
working using a standard Springboot test. If you use this library, the support of this restored. Just annotate
the `org.apache.camel.test.spring.ExcludeRoutes` to your test class containing the `CamelSpringClassRule`. 

## Installation

Put the following dependency to your Maven POM file:

    <dependency>
      <groupId>io.toolisticon.camel</groupId>
      <artifactId>camel-spring-boot-test-rule</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <scope>test</scope>
    </dependency>
