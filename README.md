# api.SearchEngineParser
This api parses SearchEngine against a given keyword and returns the page ranking(s) of a given company from the Search Result.
This is the API which actually responds to the web.

To Run the App :

IIS/WebDeploy: We can webdeploy it from visual studio.=>Right clock on the Project in Solution Explorer then click on Publish.

To test:
Please open an instance of PostMan:
-Select POST as HttpMethod.
-Give the url as http://localhost/Api.SearchEngineParser/v1/search-engine-parser/rankings
-Go to the Body,select JSON(application/json) from drop down in right side
-Give the below json structure in the Body section:
{
	keyWord: "online+title+search",
	searchEngineUrl: "https://www.google.com.au/search?num=100&q=",
	companyUrl: "www.infotrack.com.au"
}
Expected Output:"7,8,9"..else if if does not come in google search=>""

Project Details:

I have tried to use Strategy Pattern for the WebAPI logic. Due to this if we have a new requirement in the future to add one more type of SearchEngines like Bing etc,just we need to extend ISearchEngineParserStrategy. I believe thus we also adhere to the Open Closed Principle in SOLID principles.

There is lot more that can be done with the project, but due to limited scope, I am listing them.

-Basic Authentication - Using OWIN Middleware we can also have a middleware which will check for basic authentication.
-CSRF/AntiForgery token implementation between MVC Web project and API using OWIN middleware
-Wrapping the responses in API in a special class which also has validation errors sent to the front-end.
-On the UI - we can have extensive logic to handle Http StatusCodes and display suitable error messages. Currently it doesn't show any error messages if the WebAPI throws Http errors (BadRequest, InternalServer).
