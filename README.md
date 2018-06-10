# SP-Javascript

<h3>Rest basic call sharepoint list</h3>
<pre>
		    $.ajax({
		        url: _spPageContextInfo.webAbsoluteUrl + "/_api/web/...list...",
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
<h3>Get IMG url form Document Library</h3>
<pre>
		function getalldata(subsiteNow) 
		{ 
		    clientContext = new SP.ClientContext(subsiteNow);
			var web = clientContext.get_web();
			var myList = web.get_lists().getByTitle(ListName);
			var query = new SP.CamlQuery(); 
			query.set_viewXml('<View><Query><Where></Where></Query><RowLimit>2</RowLimit></View>');
          	ListItem = myList.getItems(query); 
			clientContext.load(ListItem); 
			clientContext.executeQueryAsync(mySuccessFunction, myFailFunction);
			
		}
        	function mySuccessFunction(sender, args) 
		{
			var cleanurlImageF = '';
			var listItemEnumerator = ListItem.getEnumerator();
			while (listItemEnumerator.moveNext())        
			{
				var item = listItemEnumerator.get_current();
				var ID = item.get_item('ID');
				var PublishingRollupImage = item.get_item('PublishingRollupImage');
				if(PublishingRollupImage != null){
					var urlImage = PublishingRollupImage.match("src=\"(.*)\"\\s");
					var cleanurlImage = urlImage[1].split(" "); // Prevent Sharepoint resize tag
					cleanurlImageF = cleanurlImage[0].toString().replace('"','');
				}
				else{
					cleanurlImageF = defaultIMG;
				}
				var getURLImage = cleanurlImageF;
				var Title = item.get_item('Title');
				var Created = item.get_item('Created');
			
			  
			    //var FileRef = item.get_item('FileRef');
			    //var FileDirRef = item.get_item('FileDirRef');
			    //var foldername = '';
			   
        		}
		}
</pre>
