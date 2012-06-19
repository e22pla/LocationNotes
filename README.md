### [Live Demo] (http://netmera.com/netmeraJsTest)

# What is that?

[Netmera] (http://netmera.com) is a cloud platform (PaaS) optimized for mobile applications. Netmera offers a cloud based content & data repository. With simple APIs and mobile SDKs it is easy to store, retrieve, search and query data & content on the cloud.

A sample application that uses Netmera’s JS API. Simply it keeps geo-location code and small notes that added by users on cloud. Also it can search on map and shows the contents within 5 kilometers radius of users current location.

Netmera allows circular search with few lines of code..
try {
  ContentService service = new ContentService("Blog");
		
	NetmeraGeoLocation loc = new NetmeraGeoLocation(41, 28);
		
	List < ContentContext > ctxList = service.
		circleSearch(loc, 10, "loc");

} catch (NetmeraException ex) {
	// Handle exception
}						
It searches the content by taking given location as a base and retrieves the content that located given distance far away.
