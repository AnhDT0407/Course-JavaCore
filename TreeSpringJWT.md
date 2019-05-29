```
springboot-jwt-starter/
 ├──src/                                                        * our source files
 │   ├──main
 │   │   ├──java.com.bfwg
 │   │   │   ├──config
 │   │   │   │   └──WebSecurityConfig.java                      * config file for filter, custom userSerivce etc.
 │   │   │   ├──model
 │   │   │   │   ├──Authority.java
 │   │   │   │   ├──UserTokenState.java                         * JWT model
 │   │   │   │   └──User.java                                   * our main User model.
 │   │   │   ├──repository                                      * repositories folder for accessing database
 │   │   │   │   └──UserRepository.java
 │   │   │   ├──rest                                            * rest endpoint folder
 │   │   │   │   ├──AuthenticationController.java               * auth related REST controller, refresh token endpoint etc.
 │   │   │   │   └──UserController.java                         * REST controller to handle User related requests
 │   │   │   ├──security                                        * Security related folder(JWT, filters)
 │   │   │   │   ├──auth
 │   │   │   │   │   ├──JwtAuthenticationRequest.java           * login request object, contains username and password
 │   │   │   │   │   ├──RestAuthenticationEntryPoint.java       * handle auth exceptions, like invalid token etc.
 │   │   │   │   │   ├──TokenAuthenticationFilter.java          * the JWT token filter, configured in WebSecurityConfig
 │   │   │   │   │   └──TokenBasedAuthentication.java           * this is our custom Authentication class and it extends AbstractAuthenticationToken.
 │   │   │   │   └──TokenHelper.java                             * token helper class
 │   │   │   ├──service
 │   │   │   │   ├──impl
 │   │   │   │   │   ├──CustomUserDetailsService.java           * custom UserDatilsService implementataion, tells formLogin() where to check username/password
 │   │   │   │   │   └──UserServiceImpl.java
 │   │   │   │   └──UserService.java
 │   │   │   └──Application.java                                * Application main enterance
 │   │   └──recources
 │   │       ├──static                                          * static assets are served here(Angular and html templates)
 │   │       ├──application.yml                                 * application variables are configured here
 │   │       └──import.sql                                      * h2 database query(table creation)
 │   └──test                                                    * Junit test folder
 └──pom.xml                                                     * what maven uses to manage it's dependencies
```
