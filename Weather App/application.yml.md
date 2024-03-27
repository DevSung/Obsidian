server:  
  port: 8080  
  
spring:  
  # H2 Database  
  datasource:  
    driver-class-name: org.h2.Driver  
    url: 'jdbc:h2:mem:weather'  
    username: sa  
    password: 1234  
  
  # H2 Console  
  h2:  
    console:  
      enabled: true  
      path: /h2-console  
  
  # JPA  
  jpa:  
    database-platform: org.hibernate.dialect.H2Dialect  
    hibernate:  
      ddl-auto: create  
    properties:  
      hibernate:  
        format_sql: true  
        show_sql: true  
      open-in-view: false  
  
logging:  
  level:  
    org:  
      hibernate:  
        SQL: debug  
        type.descriptor.sql: trace