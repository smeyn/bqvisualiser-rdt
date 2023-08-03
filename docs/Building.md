

# Hosting 
The application is a Single Page Application without a backend. It can be built and deployed to any webserver that is capable of serving static pages,
such as:

* Apache
* Tomcat
* IIS

## Client ID

The app has two options to retrieve queryplans directly from BigQuery:

1. via listing queries in projects,  or
2. direcly usi g the query job id

For either of these, the app needs to authenticate with GCP so the app can access teh BigQuery REST API. 
To be able to access the BigQuery REST API you need to have create an OAuth client. Create this in the Google Cloud
Console under `APIs & Services > Credentials`.

When setting up the Client ID :

* the Authorized JavaScript origins
needs to be set to the URL from where the app is downloaded.

* Authorized redirect URIs need to be set to:

    *  [download URL] 
    *  [download URL]/ 
    *  [download URL]/jobs

Once done, set the value for **clientId** in the file `./environments/environment.prod.ts` to 
the **ClientId** value in the console's Credential page

     clientId:'50<XYZ>.apps.googleusercontent.com',
  

## Building
Requires the Angular application needs to be installed.

Compile with
  `ng build --prod`

The output will be in the `dist` directory. Deploy its contents to the web server  