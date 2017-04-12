---
id: 245
title: Golang Json Parsing
date: 2017-04-12
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=245
permalink: /2017-04-12-golang-json-parser
categories:
  - golang
  - json
tags:
  - golang
  - json
---
Recently I decided to rebuild my LED board software.  Instead of building a large executable and web service, I decided to cut down the code.  I used just small executables and ran them on a cron job instead.  So I would do something like:

1.  Executable gets time/weather/message.
2.  Sends this output to a web service.
3.  The message is then put on a message queue.
4.  An executable that communicates with the LED board listens for messages.

So in order to handle all this message passing, I decided to use JSON.  There are ways to find the data you need in JSON:

1.  Regex (dont do this)
2.  Model binding (very popular route)
3.  Extract values based on a dictionary (what I will talk about today)

Number 1 is out already.  Json could change its format and make the regex useless.  Number 2 would be more appropriate if I had reuse / lots of values to extract out of the json file.  Number 3 is what I wanted to do.  Just grab a value or 2 out and that's it. In other languages, especially dynamic-typed languages, this is easy.  For a statically typed language, it gets alittle harder.  Here is what I mean:

```
{
  "My":"Value"
}
```

Say if I wanted the value of My in the json file.  In most languages it is a matter of accessing the dictionary with the key of "My":

```
var apiResp map[string]interface{}

if err := json.Unmarshal([]byte(body), &apiResp); err != nil {
  log.Fatal(err)
}

temperature = apiResp["My"].(string)
```

In the code above, we convert the json string "body" into a map of strings with an open interface.  This allows us to grab the value from apiResp as if it was a dictionary.  Now what happens if we complicate matters more:

```
body := `{"coord":{"lon":-83.15,"lat":42.66},"weather":[{"id":800,"main":"Clear","description":"clear sky","icon":"01d"}],"base":"stations","main":{"temp":279.62,"pressure":1013,"humidity":36,"temp_min":278.15,"temp_max":281.15},"visibility":16093,"wind":{"speed":6.7,"deg":330,"gust":12.9},"clouds":{"all":1},"dt":1491586560,"sys":{"type":1,"id":1460,"message":0.0052,"country":"US","sunrise":1491562970,"sunset":1491610001},"id":5007402,"name":"Rochester Hills","cod":200}`
```

If I want the temperature, I would have to get "main", which is another dictionary, then I would be able to access "temp" as a float64.  Gets more complicated if I want the description of the conditions because "weather" is an array.  But don't worry, I can up with an awesome mind saving way to grab values from a json file without having to create a model to bind to.  Here are the tips:

1.  If the value is a string
 *  Just use the dictionary like above but add string as the type
 *  Example: dictionary["My"].(string)
2.  If the value is a number
 *  Same as string, but make sure to use float64, or int
 *  Example: dictionary["Temperature"].(float64)
3.  If boolean
 *  Same as above
 *  Example: dictionary["Temperature"].(boolean)
4.  If Object
 *  This will be a map, so use the structure map[string]interface{}
 *  Example: apiResp["main"].(map[string]interface{})
5.  If array
 *  Slightly different from object, it will be converted to an array
 *  Example: apiResp["weather"].([]interface{})

These might get more complicated if there are nulls and other scenarios, but this is 80% of all values.  Want a piece of code to test out?  Try this:

```
package main

import(
	"fmt"
	"encoding/json"
	"log"
)

func main() {
	body := `{"coord":{"lon":-83.15,"lat":42.66},"weather":[{"id":800,"main":"Clear","description":"clear sky","icon":"01d"}],"base":"stations","main":{"temp":279.62,"pressure":1013,"humidity":36,"temp_min":278.15,"temp_max":281.15},"visibility":16093,"wind":{"speed":6.7,"deg":330,"gust":12.9},"clouds":{"all":1},"dt":1491586560,"sys":{"type":1,"id":1460,"message":0.0052,"country":"US","sunrise":1491562970,"sunset":1491610001},"id":5007402,"name":"Rochester Hills","cod":200}`

	var temperature float64
	var conditions string
	var apiResp map[string]interface{}

	if err := json.Unmarshal([]byte(body), &apiResp); err != nil {
		log.Fatal(err)
	}

	fmt.Println("Starting...")
	// main -> temp
	temperature = apiResp["main"].(map[string]interface{})["temp"].(float64)
	// weather -> array -> conditions
	conditions  = apiResp["weather"].([]interface{})[0].(map[string]interface{})["main"].(string)

	fmt.Println("Temperature: ",  temperature, ", Conditions: ", conditions)
}
```

You could also use the golang playground: [https://play.golang.org/p/Xue8kN8-j3](https://play.golang.org/p/Xue8kN8-j3)
