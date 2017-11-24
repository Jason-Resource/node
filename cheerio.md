```js
var cheerio = require('cheerio');

var $ = cheerio.load(body);
var time = $('.time', '.Info').text();
var source = $('div.source > img', '.Info').attr('alt');
var content = $('#ContentBody').html();
$('#pagerNoDiv > span').text()
$('a.page-btn').last().prev().text()

var list = $('#newsListContent').find('li');
list.each(function(i, element){
    var title = $('p.title > a', element).text().trim();
    var contentU = $('p.title > a', element).attr('href');
});

//**************************** */
var cheerio = require('cheerio'),
$ = cheerio.load('<h2 class="title">Hello world</h2>');

$('h2.title').text('Hello there!');
$('h2').addClass('welcome');

$.html();
//=> <h2 class="title welcome">Hello there!</h2>

//---------------------------------------------------
//去除
$("span:contains('相关报道>>>')").parents('div#ContentBody').remove();

$('#ContentBody > div.abstract').remove();

$('.EmImageRemark').parent().remove();
$("center > img[alt^='K图']").parent().remove();

$('#ContentBody').html();



var req = request.get(url).pipe(iconv.decodeStream('utf8')).collect(function (err, body) {
if(err){
    console.error("content page error:", err);
    return;
}

var $ = cheerio.load(body);
var content = $('#ContentBody').html();

});

req.on('error', function (e) {
console.log('Problem with request: ' + e.message);
});
req.on('timeout', function (e) {
console.log('request timeout: ' + e.message);
});
```
