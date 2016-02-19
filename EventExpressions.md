## What is an Event Expression ##

In [JSON Rules](http://code.google.com/p/jsonrules/wiki/RuleLanguage) an !**EventExpression** is a JSON object with the following properties (with the same meaning as in the W3C DOM Events specification):
  * _eventType_ - is a string attribute capturing the type of the event. This event type can be a DOM Event type (See [List of Complete Event Types](http://www.w3.org/TR/DOM-Level-3-Events/events.html#Events-EventTypes-complete)) but also a user-defined JavaScript event.
  * _eventTarget_ - is a [JSONTerm](JSONTerm.md). When the event type is a user-defined JavaScript event, the target can be any JavaScript object in JSON notation.

## How are they used ##
Properties of event expressions are matched  at the run time against the incoming DOM events or user-defined events. Their values are used in the rule conditions and actions.
<pre>
// When a click event occurs,<br>
// If the event occurs on an anchor element, and<br>
// its href attribute matches a specific regular expression<br>
// (rudimentary check that the link is an inbox Yahoo message link)<br>
// then call append() with the message subject as parameter.<br>
<br>
{"id":"rule102",<br>
"appliesTo":["http://mail.yahoo.com/"],<br>
"eventExpression": { "eventType": "click",<br>
"eventTarget": "$X"<br>
},<br>
"conditions":" ["$X:a(href == 'match(showMessage\?fid=Inbox)'"],<br>
"actions":["append($X.textContent)"]<br>
}<br>
</pre>