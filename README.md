# Edge-DevPortal-Smartdocs-ModelPlus

This is a modified SmartDocs model.js , for the Apigee Dev portal. Currently a work-in-progress.

The goal is to allow smartdocs to render the method-level pages nicely, when the request payload is of type "application/xml".

## History

[The original question](https://community.apigee.com/questions/48733/how-to-show-xml-in-body-request-in-apigee-smartdoc.html) on [community.apigee.com](https://community.apigee.com) asked, how can we get SmartDocs in the Drupal-based Apigee Edge devportal to display sample payloads in XML?

The SmartDocs logic, embedded in DRUPAL_ROOT/profiles/apigee/modules/custom/devconnect/smartdocs , is the magic that renders these nodes in Drupal.  The "sample payloads" are generated in the browser via some slick Javascript, that inspects the Schema and generates a JSON payload that matches the schema.

The goal is to have a sample payload that does the right thing - generate XML samples - for requests that have application/xml content-types.

Breaking down the requirements.

* when the only content-type is application/xml or text/xml, then the sample should be rendered as an XML document
* the CodeMirror editor needs to be placed into XML mode, when the payload is XML
* if multiple content-types are accepted, then when toggling between json and XML, the sample payload ought to toggle as well. And the CodeMirror mode.
* Anything else?

So far, the current implementation has been tested with a single sample OpenAPI Spec, [located here](https://api.myjson.com/bins/10k6cr).
Which means, this is really a proof of concept.  Not working code. Not suitable for production use. We can aspire to deliver something more generally usable. To get there, I will need a number of sample specifications.


## Bugs


* To this point, the testing is wholly inadequate.