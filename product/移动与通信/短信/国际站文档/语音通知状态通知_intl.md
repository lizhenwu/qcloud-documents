## Protocol Descriptions
<table style="display:table;width:100%">
  <tbody>
    <tr>
      <td style="width:15%;">
        Protocol
      </td>
      <td>
        HTTP JSON
        <br />
      </td>
    </tr>
    <tr>
      <td>
        Encoding format
      </td>
      <td>
        UTF8
      </td>
    </tr>
    <tr>
      <td>
        URL
      </td>
      <td>
		  For example: https://yun.tim.qq.com/voice/voicecallback
      </td>
    </tr>
    <tr>
      <td>
        API description
      </td>
      <td>
      After a voice notification is sent to a user, Tencent Cloud SMS service notifies the business side of the delivery status of voice notification by calling back the service URL.
      </td>
    </tr>
  </tbody>
</table>

## Request Packet
The packet is in JSON format with the following parameters:
```
{
    "voiceprompt_callback": {
        "result": "0",  //0: Answered; 1: Not answered; 2: Exceptional
        "callid": "xxxxxx", //Indicate the ID of this delivery
        "mobile": "13xxxxxxxxx", //Mobile number
        "nationcode": "86", //Country code
        "call_from": "", //Calling number
        "start_calltime": "1470197196", //Time to start a voice notification call
        "end_calltime": "1470197221", //Time to end a voice notification call
        "accept_time": "1470197211", //Time when a user answered the call
        "fee": "1"//Charged duration (in min)
    }
}
```

## Response Packet
When receiving a callback request, the third party needs to give a response to Tencent Cloud SMS service in the following format:
```
{ 
    "result": 0, //0: Successful. Other values: Failed
    "errmsg": "OK" //The specific error message when the "result" is not 0
}
```
