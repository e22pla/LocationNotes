### [Live Demo] (http://netmera.com/netmeraJsTest)

# What is that?

[Netmera] (http://netmera.com) is a cloud platform (PaaS) optimized for mobile applications. Netmera offers a cloud based content & data repository. With simple APIs and mobile SDKs it is easy to store, retrieve, search and query data & content on the cloud.

LocationNotes is a sample application that uses Netmera’s JS API. Simply it keeps geo-location code and small notes that added by users on cloud. Also it can search on map and shows the contents within 5 kilometers radius of users current location.

Netmera allows circular search with few lines of code.
			
			var contentService = new x.contentService("Notes");
			contentService.setMax(10);
			contentService.setPage(page);

			contentService.circleSearch(x.geoLocation(location.latitude, location.longitude), 5, "noteLocation", function() {
				var entries = contentService.getEntries();
				var totalResults = contentService.getTotalResults();
				if (totalResults > 0) {
					$.each(entries, function(key, val) {
						var myLatlng = new google.maps.LatLng(val.get("latitude"), val.get("longitude"));
						var marker = new google.maps.Marker({
							position: myLatlng,
							map: mapCanvas
						});
						google.maps.event.addListener(marker, 'click', function() {
							detailPage(val);
						});
					});
				}
			});
			
It searches the content by taking given location as a base and retrieves the content that located given distance far away.
