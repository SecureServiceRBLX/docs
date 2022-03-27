# Promote [POST]

```/api/promote/```

This endpoint promotes the specified user.

## Request Body

| Body      | Description           | Type              |
| ----------- | ---------------------|--------------- |
| `key`       | Your paid gamekey | `STRING` | 
| `user`       | The user who you want to promote | `INTEGER` |
| `group`    | The group which the user is in | `INTEGER` | 

## Examples

=== "Javascript"
    ```javascript
    async function sendReqest() {
        const response = await fetch('http://node.justbillyh.xyz:2012/api/promote', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json'
            },
            body: JSON.stringify({ key: 'GAMEKEY', user: 'USER ID HERE', group: 'GROUP ID HERE' })
        });
        return response.json();
    }
    ```
=== "Luau/Lua 5.2"
    ```lua
    local HttpService = game:GetService("HttpService")
    local URL = "http://node.justbillyh.xyz/api/promote"
    local function request()
	local response = HttpService:RequestAsync(
		{
			Url = URL, 
			Method = "POST",
			Headers = {
				["Content-Type"] = "application/json" 
			},
			Body = HttpService:JSONEncode({key = "GAMEKEY", user = "USER ID HERE", group = "GROUP ID HERE"})
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

    r = requests.post('http://node.justbillyh.xyz:2012/api/promote', data={'key': 'GAMEKEY', 'user': 'USER ID HERE', 'group': 'GROUP ID HERE'})
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
            "user": "USER ID HERE",
            "group": "GROUP ID HERE",
        })
        responseBody := bytes.NewBuffer(postBody)
        resp, err := http.Post("http://node.justbillyh.xyz/api/promote", "application/json", responseBody)
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
