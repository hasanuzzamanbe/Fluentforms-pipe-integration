## Add this to the HTML field on your form editor
```
<link rel="stylesheet" href="//cdn.addpipe.com/2.0/pipe.css">
<div id="fluentformVdoRecoder"> </div>
<script type="text/javascript" src="//cdn.addpipe.com/2.0/pipe.js"></script>

```



## Paste this script bellow on your custom JSS field and replace the "ACCOUNT_HASH_ID". 
## Ensure that the form have at least one hidden field 
```
var pipeParams = {
    size:{width:640,height:390}, 
    qualityurl:"avq/720p.xml", 
    accountHash:"ACCOUNT_HASH_ID", 
    eid:"U3fR2p", 
    mrt:120
};

// For Fluentforms
PipeSDK.insert("fluentformVdoRecoder",pipeParams,function(recorderObject){
    var accountHash = pipeParams.accountHash;
    recorderObject.onSaveOk = function onSaveOk(streamName, streamDuration, userId, cameraName, micName, recorderId, audioCodec, videoCodec, fileType, videoId, audioOnly, location) {
	jQuery( "[name='hidden']" )[0].value = "https://"+ audioOnly+ "/" + accountHash + "/" + streamDuration + ".mp4"
    }
});
```
