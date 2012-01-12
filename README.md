
First: jquery.couch,js is a wrapper for couchdb API functions based on jquery functioniality.

jquery.couch.js documentation can found here:

jquery.couch.extended.js - is a extension to allow extend jquery.couch.db object with own functions and implements
													 helper functions for install / updating a design doc and removeing a attachement.
													

new provided functions:

$.couch.functions_toString - Util function to translate all functions in an object to their String Form
 <pre><code>
  $.couch.functions_toString({
    testfn: function(){ alert("test function") }
  });
 </code></pre>

$.couch.request - Util function to request an couchdb REST Endpoint



$.couch.db.installDesignDoc - install or update an design doc

<pre><code>
 var $db = $.couch.db("default");
 $db.installDesignDoc({
 	"_id": "_design/test",
 	"views": {
 		"byCollection": {
 			"map": function(doc, req){
 				if (doc.collection) {
 					emit(doc.collection, doc);
 				}
 			}
 		}
 	}
 }, {
 	success: function(){ alert("Design Document installed/updated."); },
 	error:   function(){ alert("Design Document can´t installed."); }
 } );
</code></pre>

$.couch.db.removeAttachement - remove an Attachement Document
<code>removeAttachement({_id:"mydoc/attachement", _rev: "1-2345"})</code>