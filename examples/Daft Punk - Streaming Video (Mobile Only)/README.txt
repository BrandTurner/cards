#Flock Card (API Calling)

The Flock Card is a simple example of showing API calls from a card.

Please note: the API calling features are a work in progress. Cards using these features are subject to break
until the final version is released. Also, to test API calls, you'll need the latest internal iOS build
of the iPhone Twitter client. (Go to http://go/ios to download it, or talk to your friendly Twitter Developer Advocate
for a test device.)

## The example server

This example is hard-coded to communicate to a test server:

	http://www.birdops.com/card/api/1

This is the response from the server:

	{"count": "15", "response": "You got it!"}

The server will update the count on each request (roughly).

## Testing the Card

To test your Card, open it on the Twitter App build and load it. Next, tap on the image to trigger the API call.

Look in the API Calling Reference for more details on API Calls. Note that the APIs are rapidly changing, so the latest docs may be out of date.

## How it works

The Twitter Card system allows API calls to third party servers. An action executing a API call looks like this:

  <action id="get_coupon">
    <apiRequest onRequestSuccess="get_coupon_success" onRequestFailure="get_coupon_failure" apiEndpoint="proxy_rule" />
  </action>

Also note that there is an `<apiEndpoint>` to define how we route through our proxy. The API endpoint is defined as:

    <apiEndpoints>
        <apiEndpoint id="proxy_rule">
          <externalRequest url="http://www.birdops.com/card/api/1" method="GET">
          </externalRequest>
        </apiEndpoint>
    </apiEndpoints>




