## add this to the HTML field on your form editor
<link rel="stylesheet" href="//cdn.addpipe.com/2.0/pipe.css">
<div id="fluentformVdoRecoder"> </div>
<script type="text/javascript" src="//cdn.addpipe.com/2.0/pipe.js"></script>




## paste this script on your custom JSS field and replace the "YOUR-ACCOUNT-HASH-ID". 
## Ensure that the form have at least one hidden field 

<script type="text/javascript">
	var pipeParams = {
	    size:{width:640,height:390}, 
	    qualityurl:"avq/360p.xml", 
	    accountHash:"YOUR-ACCOUNT-HASH-ID", 
	    eid:"U3fR2p", 
	    mrt:120
	};
	PipeSDK.insert("fluentformVdoRecoder",pipeParams,function(recorderObject){
	     var accountHash = pipeParams.accountHash;
	     var baseUrl = "https://eu1-addpipe.s3.eu-central-1.amazonaws.com/";
	        recorderObject.onSaveOk = function onSaveOk(streamName, streamDuration, userId, cameraName, micName, recorderId, audioCodec, videoCodec, fileType, videoId, audioOnly, location) {
	        jQuery( "[name='hidden']" )[0].value = baseUrl + accountHash + "/" + streamDuration + ".mp4"
	     }
	});
</script>
