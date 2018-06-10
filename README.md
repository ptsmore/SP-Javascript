# SP-Javascript

<h3>Rest get IMG url form Document Library</h3>
<pre>
		    $.ajax({
		        url: _spPageContextInfo.webAbsoluteUrl + "/_api/web/docLib",
		        type: "GET",
		        headers: { "accept": "application/json;odata=verbose" },
		        success: function (data) {
		            var lstItem = data.d.results;
		            for (var i = 0; i < lstItem.length ; i++) {
		                //lstItem[i].Url
		            }
		        },
		        error: function (error) { alert(JSON.stringify(error)); }
		    });
		
</pre>
