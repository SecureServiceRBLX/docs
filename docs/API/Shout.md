# Shout [POST]

```/api/shout/```

This endpoint shouts a specified message in the specified group.

## Request Body

| Body      | Description           | Type              |
| ----------- | ---------------------|--------------- |
| `key`       | Your paid gamekey | `STRING` | 
| `group`    | The group which you want to look for the join request | `INTEGER` | 
| `body`    | The message you want posted on the shout | `STRING` |

## Examples

=== "Javascript"
    ```javascript
    async function sendReqest() {
        const response = await fetch('http://node.justbillyh.xyz:2012/api/shout', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json'
            },
            body: JSON.stringify({ key: 'GAMEKEY', group: 'GROUP ID HERE', body: 'SHOUT MESSAGE HERE' })
        });
        return response.json();
    }
    ```
=== "Luau"
    ```lua
    local HttpService = game:GetService("HttpService")
    local URL = "http://node.justbillyh.xyz/api/shout"
    local function request()
	local response = HttpService:RequestAsync(
		{
			Url = URL, 
			Method = "POST",
			Headers = {
				["Content-Type"] = "application/json" 
			},
			Body = HttpService:JSONEncode({key = "GAMEKEY", group = "GROUP ID HERE", body: "SHOUT MESSAGE HERE"})
		}
	)
         if response.Success then
            print("Status code:", response.StatusCode, response.StatusMessage)
            print("Response body:\n", response.Body)
        else
            print("The request failed:", response.StatusCode, response.StatusMessage)
        end
    end
    
    local success, message = pcall(request)
    if not success then
        print("Http Request failed:", message)
    end
    ```
=== "Python"
    ```py
    import requests

    r = requests.post('http://node.justbillyh.xyz:2012/api/shout', data={'key': 'GAMEKEY', 'group': 'GROUP ID HERE', body: 'SHOUT MESSAGE HERE'})
    ```
=== "Golang"
    ```go
    import (
        "bytes"
        "encoding/json"
        "io/ioutil"
        "log"
        "net/http"
    )

    func main() {
        postBody, _ := json.Marshal(map[string]string{
            "key":  "GAMEKEY HERE",
            "group": "GROUP ID HERE",
            "body": "SHOUT MESSAGE HERE"
        })
        responseBody := bytes.NewBuffer(postBody)
        resp, err := http.Post("http://node.justbillyh.xyz/api/shout", "application/json", responseBody)
        if err != nil {
            log.Fatalf("An Error Occured %v", err)
        }
        defer resp.Body.Close()
        body, err := ioutil.ReadAll(resp.Body)
        if err != nil {
            log.Fatalln(err)
        }
        sb := string(body)
        log.Printf(sb)
    }
    ```
