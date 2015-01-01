# HTTP-API-Web-Testing-Kit
Automation of HTTP, HTTPS, API and UI using PHPUnit, Behat, Mink, Pear and Selenium.

## Dependancies
On Mac OS X, this requires:

1. [XCode](https://developer.apple.com/xcode/downloads/)
2. [Developer Tools](http://stackoverflow.com/questions/9329243/xcode-4-4-and-later-install-command-line-tools) for XCode
3. [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html), see [documentation](http://docs.oracle.com/javase/7/docs/webnotes/install/mac/mac-jdk.html) 
4. [cURL](http://curl.haxx.se/download.html)
5. [PHP](http://php.net/manual/en/install.macosx.php)

## Installation
#### Composer

	curl http://getcomposer.org/installer | php
	php composer.phar install

Or you may need to just update to install thhe dependancies listed in `composer.json` via:

	php composer.phar update
	

#### Pear

	wget http://pear.php.net/go-pear.phar
	php go-pear.phar

#### PHPUnit 3.x & Up

	pear channel-discover pear.phpunit.de
	pear channel-discover components.ez.no
	pear channel-discover pear.symfony-project.com	
	pear install phpunit/PHPUnit

## Usage 

###Clone It

	git clone https://github.com/KnpLabs/behat-webapi-demo

###Start Selenium

	java -jar selenium-server-standalone-2.43.1.jar

###Run Tests

	bin/behat


You should see:

	Feature: I want to automate continous integration and regression tests for API and End Points
	  
	  As a tester
	  I want to evaluate API and end-points
	  So that I can automate continous integration and regression tests
	
	  @regression @smoke @POSTRequests @Staples
	  Scenario Outline: Metric Requests for Staples Accelerator  # features/AdcadeAPI.feature:8
	    Given I send a POST request to "<requestURL>" with body: # Behat\CommonContexts\WebApiContext::iSendARequestWithBody()
	      """
	      {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":80069,"key":"std.interact.expansion"},{"type":"tup","time":80275,"x":434,"y":20}]}:
	      """
	    Then the response code should be 200                     # Behat\CommonContexts\WebApiContext::theResponseCodeShouldBe()
	
	    Examples:
	      | requestURL                                                               | body                                                                                                                                                                                                                                                                                                  |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":80069,"key":"std.interact.expansion"},{"type":"tup","time":80275,"x":434,"y":20}]}:                                                                                                               |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"tdn","time":79976,"x":434,"y":20}]}                                                                                                                                                                           |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"tdn","time":3993192,"x":364,"y":577}]}                                                                                                                                                                        |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":3993291,"key":"std.interact.Slingshot_Play"},{"type":"tup","time":3993313,"x":364,"y":577},{"type":"tdn","time":3993318,"x":364,"y":577},{"type":"tup","time":3993596,"x":364,"y":577}]}          |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"tdn","time":4001108,"x":337,"y":567}]}                                                                                                                                                                        |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":4001945,"key":"std.interact.Slingshot_Launch_135848"},{"type":"tup","time":4001949,"x":301,"y":767},{"type":"tdn","time":4001950,"x":301,"y":767},{"type":"tup","time":4001971,"x":301,"y":767}]} |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"tup","time":4013077,"x":515,"y":431},{"type":"ctr","time":4013134,"key":"std.interact.SubmitScoreSlingshot"}]}                                                                                                |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":4255016,"key":"std.interact.Slingshot_PlayAgain"},{"type":"tup","time":4255022,"x":111,"y":24}]}                                                                                                  |
	      | http://ad-stage.adcade.com/2/event/81983ac5-2703-4631-b9de-19e1a724e7e6/ | {"adId":"STPALF14SLITAB72890WEB","pId":"0","startTime":1419997205271,"events":[{"type":"ctr","time":4277802,"key":"std.interact.collapse"},{"type":"tup","time":4277814,"x":661,"y":17}]}:                                                                                                            |
	
	  @regression @smoke @POSTRequests @Videos
	  Scenario Outline: Metric Requests for Refinery 29 Video H-Unit # features/AdcadeAPI.feature:28
	    Given I send a POST request to "<requestURL>" with body:     # Behat\CommonContexts\WebApiContext::iSendARequestWithBody()
	      """
	      {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":26346,"key":"std.auto.video.start.main_video"}]}:
	      """
	    Then the response code should be 200                         # Behat\CommonContexts\WebApiContext::theResponseCodeShouldBe()
	
	    Examples:
	      | requestURL                                                                | body                                                                                                                                                                                                          |
	      | https://ad-stage.adcade.com/2/event/cf7964c2-2619-42b2-9bac-81cb26d0da97/ | {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":26346,"key":"std.auto.video.start.main_video"}]}:        |
	      | https://ad-stage.adcade.com/2/event/cf7964c2-2619-42b2-9bac-81cb26d0da97/ | {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":30108,"key":"std.auto.video.1st_quartile.main_video"}]}: |
	      | https://ad-stage.adcade.com/2/event/cf7964c2-2619-42b2-9bac-81cb26d0da97/ | {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":33877,"key":"std.auto.video.2nd_quartile.main_video"}]}: |
	      | https://ad-stage.adcade.com/2/event/cf7964c2-2619-42b2-9bac-81cb26d0da97/ | {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":37641,"key":"std.auto.video.3rd_quartile.main_video"}]}: |
	      | https://ad-stage.adcade.com/2/event/cf7964c2-2619-42b2-9bac-81cb26d0da97/ | {"adId":"f2a81d25-a9cb-4404-9840-fb48db6445c7","pId":"0ed35dcb-b756-476b-aafa-2e145a3726b5","startTime":1420001669019,"events":[{"type":"ctr","time":41180,"key":"std.auto.video.complete.main_video"}]}:     |
	
	  @javascript @regression @smoke @GETRequests
	  Scenario Outline: GET 200 Requests                             # features/AdcadeAPI.feature:45
	    Given I am on "<requestURL>"                                 # FeatureContext::visit()
	    Then the response should contain "<expectedOutcome>"         # FeatureContext::assertResponseContains()
	
	    Examples:
	      | requestURL                                                                                                                       | expectedOutcome  |
	      | http://ad-prod.adcade.com/2/ad/STPALF14SLITAB72890WEB/pl/0/                                                                      | function         |
	      | http://ad-prod.adcade.com/2/tiny/STPALF14SLITAB72890WEB/pl/0/?cb=CACHEBUSTER;noMargin=true;canvasPositioning=absolute            | ADCADE=ADCADE    |
	      | https://resource.adcade.com/ad_static/lib/2.5/adcadetiny.js                                                                      | ADCADE=ADCADE    |
	      | http://ad-stage.adcade.com/2/event/imp/STPALF14SLITAB72890WEB/pl/0/?v=84532159                                                   | sessionId        |
	      | https://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/main-built.js                                                       | function         |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/logo_staples.png                                          | logo_staples.png |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/conveyor.png                                              | conveyor.png     |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/txt_timer.gif                                             | txt_timer.gif    |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/basket.png                                                | basket.png       |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/badge.png                                                 | badge.png        |
	      | http://resource.adcade.com/ad-assets/STPALF14SLITAB72890WEB/assets/img/backup.jpg                                                | backup.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/e_bg_b.jpg                                 | e_bg_b.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/e_bg_t.jpg                                 | e_bg_t.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/e_bg_r.jpg                                 | e_bg_r.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/e_bg_l.jpg                                 | e_bg_l.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/c_background.jpg                           | c_background.jpg |
	      | https://ad-stage.adcade.com/2/event/imp/f2a81d25-a9cb-4404-9840-fb48db6445c7/pl/0ed35dcb-b756-476b-aafa-2e145a3726b5/?v=44467654 | sessionId        |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/play.png                                   | play.png         |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/pause.png                                  | pause.png        |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/mute.png                                   | mute.png         |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/unmute.png                                 | unmute.png       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/close.png                                  | close.png        |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/img/poster.jpg                                 | poster.jpg       |
	      | https://resource.adcade.com/ad-assets/f2a81d25-a9cb-4404-9840-fb48db6445c7/assets/vid/video.mp4?q=3d7c2c79b16b                   | video.mp4        |
	
	38 scenarios (38 passed)
	76 steps (76 passed)
	0m9.96s