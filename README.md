<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>A simple clock</title>

</head>

<body translate="no" >
  <div id="output" 
       style=	"display: inline-block;
		font-family: monospace;
		font-size: 30px;
		text-align: right;
		color: lightgray; 
		border-radius: 10px; 
		padding: 10px; 
		background-color: rgba(0, 0, 0, 0.75);">
  </div>

  <script src='https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.18.1/moment.min.js'></script>
  <script>
// https://stackoverflow.com/questions/901115/how-can-i-get-query-string-values-in-javascript
var urlParams;
(function () {
    var match,
        pl     = /\+/g,  // Regex for replacing addition symbol with a space
        search = /([^&=]+)=?([^&]*)/g,
        decode = function (s) { return decodeURIComponent(s.replace(pl, " ")); },
        query  = window.location.search.substring(1);
    urlParams = {};
    while (match = search.exec(query))
       urlParams[decode(match[1])] = decode(match[2]);
})();
var output = document.getElementById("output");
if (urlParams["style"]) output.setAttribute("style", urlParams["style"]);
if (urlParams["bodyStyle"]) document.body.setAttribute("style", urlParams["bodyStyle"]);
var c;
setInterval(
c = function() {
	output.innerText = moment().format(urlParams["format"] || 'MMM DD, YYYY | hh:mm:ssa'
//    output.innerText = moment().format(urlParams["format"] || '');
}, 1000);
c();
  </script>
</body>
</html>
