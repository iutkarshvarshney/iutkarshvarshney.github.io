<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html b:css='false' b:responsive='true' expr:dir='data:blog.languageDirection' lang='en-US' xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
 <head>
   
   <script type='text/javascript'> var infolinks_pid = 3293110; var infolinks_wsid = 0; </script> <script src='//resources.infolinks.com/js/infolinks_main.js' type='text/javascript'/>
   
 <meta content='width=device-width, initial-scale=1' name='viewport'/>
  <b:include data='blog' name='all-head-content'/>
  <title>FREE HD YouTube Thumbnail Downloader - Save YouTube HQ Thumbnails</title>
  <meta content='FREE HD YouTube Thumbnail Downloader - Save YouTube HQ Thumbnails' name='description'/>
  <meta content='youtube thumbnail downloader apk, thumbnail download for pc, youtube thumbnail grabber, facebook thumbnail download, youtube thumbnail downloader extension, free thumbnail download, youtube thumbnail download script, youtube thumbnail background download' name='keywords'/>
  <b:skin><![CDATA[
  
    body{background:#fff}

   ]]></b:skin>
 </head>
 <body>
  <b:section class='main' id='main' showaddelement='yes'>
    <b:widget id='HTML3' locked='false' title='' type='HTML' version='1'>
      <b:widget-settings>
        <b:widget-setting name='content'>&lt;script type=&#39;text/javascript&#39;&gt;
function initDownloadLinks (e) {
    var value = document.getElementById(&quot;inputURL&quot;).value;
    console.log(value);
    var isVimeo = checkVimeo(value);
    console.log(isVimeo)
    if (isVimeo) {
        isVimeo = isVimeo[isVimeo.length - 1];
        getVimeoDetails(isVimeo);
        return 0;
    }
    var result = (extractValue(value));
    if (result === 0) {
        return 0;
    }
    appendImages(result);
    return false;
}
function initFunction () {
    documentReady();

    document.getElementById(&quot;submitButton&quot;).onclick = function (e) {
        initDownloadLinks(e);
    }
}
function setDisplay (value) {
    var arrayOfElements = document.getElementsByClassName(&#39;download-bt&#39;);
    var lengthOfArray = arrayOfElements.length;

    for (var i = 0; i &lt; lengthOfArray; i++) {
        arrayOfElements[i].style.display = value;
    }
}

    function appendVimeoVideos (hdLink, mdLink, sdLink) {
        setDisplay(&quot;none&quot;);
        document.getElementsByClassName(&#39;right-click-info&#39;)[0].style.display = &quot;block&quot;;

        document.getElementById(&quot;hdrestext&quot;).textContent = &quot;HD Image (640x480)&quot;;
        document.getElementById(&quot;sdrestext&quot;).textContent = &quot;SD Image (200x150)&quot;;
        document.getElementById(&quot;normalrestext&quot;).textContent = &quot;Normal Image (100x74)&quot;;
        document.getElementById(&quot;imgListing&quot;).style.display = &quot;block&quot;;
        document.getElementById(&quot;bottomListing&quot;).style.display = &quot;block&quot;;
        document.getElementById(&quot;topListing&quot;).style.display = &quot;block&quot;;
        var element = document.getElementById(&quot;maxres&quot;)
        element.setAttribute(&quot;src&quot;, hdLink);
        element.style.display = &quot;block&quot;;
        element = document.getElementById(&quot;hqres&quot;);
        element.setAttribute(&quot;src&quot;, sdLink);
        element.style.display = &quot;block&quot;;
        element = document.getElementById(&quot;sdres&quot;);
        element.setAttribute(&quot;src&quot;, mdLink);
        document.getElementById(&quot;extraYTImg&quot;).style.display = &quot;none&quot;;
        document.getElementById(&quot;hdreslink&quot;).style.display = &quot;none&quot;;
        document.getElementById(&quot;sdreslink&quot;).style.display = &quot;none&quot;;
        document.getElementById(&quot;hqreslink&quot;).style.display = &quot;none&quot;;
    }

    function checkVimeo (data) {
        var res = data.match(/https?:\/\/(?:www\.|player\.)?vimeo.com\/(?:channels\/(?:\w+\/)?|groups\/([^\/]*)\/videos\/|album\/(\d+)\/video\/|video\/|)(\d+)(?:$|\/|\?)/)
        return res;
    }

    function getVimeoDetails (link) {
        var xmlhttp = new XMLHttpRequest();

        xmlhttp.onreadystatechange = function () {
            if (xmlhttp.readyState == XMLHttpRequest.DONE) {   // XMLHttpRequest.DONE == 4
                if (xmlhttp.status == 200) {
                    var data = (JSON.parse(xmlhttp.responseText));
                    appendVimeoVideos(data[0].thumbnail_large, data[0].thumbnail_medium, data[0].thumbnail_small);
                }
                else if (xmlhttp.status == 400) {
                    alert(&quot;There is no video in the vimeo link you have given&quot;);
                }
                else {
                    alert(&quot;There is no video in the vimeo link you have given&quot;);
                }
            }
        };

        xmlhttp.open(&quot;GET&quot;, &#39;https://vimeo.com/api/v2/video/&#39; + link + &#39;.json&#39;, true);
        xmlhttp.send();

    }
    function isMaxResAvailable (result) {
        var img = new Image()
        img.onload = function () {
            if (this.width &lt; 1280) {

                document.getElementById(&quot;hdreslink&quot;).style.display = &quot;none&quot;;
                document.getElementById(&quot;hdrestext&quot;).textContent = &quot;High resolution not available&quot;;
                isSDAvailalbe(result);
            } else {
                document.getElementById(&quot;hdrestext&quot;).textContent = &quot;HD Image (1280x720)&quot;;
            }
        }
        img.onerror = function () {
            document.getElementById(&quot;sdrestext&quot;).textContent = &quot;High resolution not available&quot;;
            isSDAvailalbe(result);
        }
        img.src = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/maxresdefault.jpg&quot;;

    }
    function isImageAvailable () {

        alert(&quot;Please check the youtube video link. It appears the video link is broken.&quot;)


    }
    function isSDAvailalbe (result) {
        var img = new Image()
        img.onload = function () {
            if (this.width === 120 &amp;&amp; this.height === 90) {
                document.getElementById(&quot;sdrestext&quot;).textContent = &quot;Standard Quality not available&quot;;
                document.getElementById(&quot;sdreslink&quot;).style.display = &quot;none&quot;;
            } else {
                document.getElementById(&quot;sdrestext&quot;).textContent = &quot;SD Image (640x480)&quot;;
            }
        }
        img.onerror = function () {
            document.getElementById(&quot;sdrestext&quot;).textContent = &quot;Standard Quality not available&quot;;

        }
        img.src = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/sddefault.jpg&quot;;

    }

    function appendImages (result) {
        //document.getElementsByClassName(&quot;download-btn&quot;).style.display = &quot;block&quot;;
        setDisplay(&quot;block&quot;);

        document.getElementsByClassName(&#39;right-click-info&#39;)[0].style.display = &quot;none&quot;;

        document.getElementById(&quot;hdreslink&quot;).style.display = &quot;inline&quot;;
        document.getElementById(&quot;sdreslink&quot;).style.display = &quot;inline&quot;;
        document.getElementById(&quot;hqreslink&quot;).style.display = &quot;inline&quot;;
        document.getElementById(&quot;inputURL&quot;).value = &quot;https://youtube.com/watch?v=&quot; + result;
        document.getElementById(&quot;imgListing&quot;).style.display = &quot;block&quot;;
        document.getElementById(&quot;bottomListing&quot;).style.display = &quot;block&quot;;
        document.getElementById(&quot;topListing&quot;).style.display = &quot;block&quot;;
        document.getElementById(&quot;hdrestext&quot;).textContent = &quot;HD Image (1280x720)&quot;;
        document.getElementById(&quot;sdrestext&quot;).textContent = &quot;SD Image (640x480)&quot;;
        document.getElementById(&quot;normalrestext&quot;).textContent = &quot;Normal Image (480x360)&quot;;
        document.getElementById(&quot;maxres&quot;).setAttribute(&quot;src&quot;, &quot;https://img.youtube.com/vi/&quot; + result + &quot;/maxresdefault.jpg&quot;);//.removeClass(&quot;disabled&quot;);
        document.getElementById(&quot;sdres&quot;).setAttribute(&quot;src&quot;, &quot;https://img.youtube.com/vi/&quot; + result + &quot;/sddefault.jpg&quot;);
        document.getElementById(&quot;hqres&quot;).setAttribute(&quot;src&quot;, &quot;https://i3.ytimg.com/vi/&quot; + result + &quot;/hqdefault.jpg&quot;);
        document.getElementById(&quot;mqres&quot;).setAttribute(&quot;src&quot;, &quot;https://img.youtube.com/vi/&quot; + result + &quot;/mqdefault.jpg&quot;);
        document.getElementById(&quot;defres&quot;).setAttribute(&quot;src&quot;, &quot;https://img.youtube.com/vi/&quot; + result + &quot;/default.jpg&quot;);

	document.getElementById(&quot;hdreslink&quot;).href = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/maxresdefault.jpg&quot;;
        document.getElementById(&quot;sdreslink&quot;).href = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/sddefault.jpg&quot;;
        document.getElementById(&quot;hqreslink&quot;).href = &quot;https://i3.ytimg.com/vi/&quot; + result + &quot;/hqdefault.jpg&quot;;
        document.getElementById(&quot;mqreslink&quot;).href = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/mqdefault.jpg&quot;;
	document.getElementById(&quot;defreslink&quot;).href = &quot;https://img.youtube.com/vi/&quot; + result + &quot;/default.jpg&quot;;
        isMaxResAvailable(result);

        document.getElementById(&quot;extraYTImg&quot;).style.display = &quot;block&quot;;
    }

    function extractValue (data) {
        console.log(data)
        var res = data.match(/(?:https?:\/{2})?(?:w{3}\.)?youtu(?:be)?\.(?:com|be)(?:\/watch\?v=|\/)([^\s&amp;]+)/)
        if (res == undefined) {
            alert(&quot;Please check the URL you have entered&quot;);
            return 0;
        }
        return res[1];
    }


    function showAlertInfo (info) {
        var div = document.createElement(&quot;div&quot;);
        div.setAttribute(&quot;class&quot;, &quot;alert alert-info alert-dismissable fade in &quot; + info);
        div.setAttribute(&quot;id&quot;, &quot;alertBanner&quot;);
        var aTag = document.createElement(&quot;a&quot;);
        a.setAttribute(href, &quot;#&quot;);
        a.setAttribute(&quot;class&quot;, &quot;close&quot;);
        a.setAttribute(&quot;aria-label&quot;, &quot;close&quot;);
        a.setAttribute(&quot;text&quot;, &quot;x&quot;);
        a.setAttribute(&quot;data-dismiss&quot;, &quot;alert&quot;);
        div.appendChild(a);
        div.appendChild(html);
        document.getElementById(&quot;images&quot;).appendChild(div);
    }
    function documentReady () {

        (function () {
            function getQueryStringValue (key) {
                return decodeURIComponent(window.location.search.replace(new RegExp(&quot;^(?:.*[&amp;\\?]&quot; + encodeURIComponent(key).replace(/[\.\+\*]/g, &quot;\\$&amp;&quot;) + &quot;(?:\\=([^&amp;]*))?)?.*$&quot;, &quot;i&quot;), &quot;$1&quot;));
            }
            var id = getQueryStringValue(&#39;id&#39;);
            var type = getQueryStringValue(&quot;type&quot;);
            if (type == &quot;vimeo&quot;) {
                document.getElementById(&quot;inputURL&quot;).value = &quot;https://vimeo.com/&quot; + id
                var vimId = checkVimeo(&quot;https://www.vimeo.com/&quot; + id);
                vimId = vimId[vimId.length - 1];

                getVimeoDetails(vimId);
                return 0;
            }
            if (id !== &quot;&quot;) {
                appendImages(id);
            }

        }());
    };
    initFunction();
&lt;/script&gt;</b:widget-setting>
      </b:widget-settings>
      <b:includable id='main'>
  <!-- only display title if it's non-empty -->
  <b:if cond='data:title != &quot;&quot;'>
    <h2 class='title'><data:title/></h2>
  </b:if>
  <div class='widget-content'>
    <data:content/>
  </div>

  
</b:includable>
    </b:widget>
    <b:widget id='HTML2' locked='false' title='' type='HTML' version='1'>
      <b:widget-settings>
        <b:widget-setting name='content'>&lt;style&gt;
*{-webkit-box-sizing:border-box;-moz-box-sizing:border-box;box-sizing:border-box;line-height:1.5}html,body{color:#555;margin:0;padding:0}html{font-family:&quot;Libre Baskerville&quot;,&quot;Times New Roman&quot;,Times,serif;font-size:14px;overflow-y:scroll}@media (min-width: 600px){html{font-size:16px}}body{-webkit-text-size-adjust:100%}h1,h2,h3,h4,h5,h6{color:#353535;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif;line-height:normal}a{color:#4a9ae1;text-decoration:none}blockquote{border-left:0.25rem solid #e5e5e5;color:#979797;margin:.8rem 0;padding:.5rem 1rem}blockquote p:last-child{margin-bottom:0}@media (min-width: 600px){blockquote{padding:0 5rem 0 1.25rem}}img{display:block;margin:0 0 1rem;max-width:100%}td{vertical-align:top}pre,code{font-family:Menlo,Monaco,monospace}code{background-color:#f9f9f9;border-radius:3px;color:#bf616a;font-size:85%;padding:.25em .5em}pre{margin:0 0 1rem}pre code{background-color:transparent;color:inherit;font-size:100%;padding:0}.highlight{background-color:#f9f9f9;border-radius:3px;line-height:1.4;margin:0 0 1rem;padding:1rem}.highlight pre{margin-bottom:0;overflow-x:auto}.highlight .lineno{color:#aaa;display:inline-block;padding:0 .75rem 0 .25rem;-webkit-user-select:none;-moz-user-select:none;user-select:none}.post{padding:3rem 0}.post-info{color:#aaa;font-family:Palatino,&quot;Palatino LT STD&quot;,&quot;Palatino Linotype&quot;,&quot;Book Antiqua&quot;,&quot;Georgia&quot;,serif;letter-spacing:0.5px;text-align:center}.post-info span{font-style:italic}.post-title{color:#353535;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif;font-size:4rem;margin:1rem 0;text-align:center}.post-line{border-top:0.4rem solid #353535;display:block;margin:0 auto 3rem;width:4rem}.post p{margin:0 0 1rem;text-align:justify}.post a:hover{text-decoration:underline}.post img{margin:0 auto 0.5rem}.post img+em{color:#aaa;display:block;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif;font-size:0.9rem;font-style:normal;text-align:center}.post img.emoji{display:inline-block;left:0;transform:none;width:1rem;height:1rem;vertical-align:text-top;padding:0;margin:0}.highlight .hll{background-color:#ffc}.highlight .c{color:#999}.highlight .err{color:#a00;background-color:#faa}.highlight .k{color:#069}.highlight .o{color:#555}.highlight .cm{color:#09f;font-style:italic}.highlight .cp{color:#099}.highlight .c1{color:#999}.highlight .cs{color:#999}.highlight .gd{background-color:#fcc;border:1px solid #c00}.highlight .ge{font-style:italic}.highlight .gr{color:#f00}.highlight .gh{color:#030}.highlight .gi{background-color:#cfc;border:1px solid #0c0}.highlight .go{color:#aaa}.highlight .gp{color:#009}.highlight .gu{color:#030}.highlight .gt{color:#9c6}.highlight .kc{color:#069}.highlight .kd{color:#069}.highlight .kn{color:#069}.highlight .kp{color:#069}.highlight .kr{color:#069}.highlight .kt{color:#078}.highlight .m{color:#f60}.highlight .s{color:#d44950}.highlight .na{color:#4f9fcf}.highlight .nb{color:#366}.highlight .nc{color:#0a8}.highlight .no{color:#360}.highlight .nd{color:#99f}.highlight .ni{color:#999}.highlight .ne{color:#c00}.highlight .nf{color:#c0f}.highlight .nl{color:#99f}.highlight .nn{color:#0cf}.highlight .nt{color:#2f6f9f}.highlight .nv{color:#033}.highlight .ow{color:#000}.highlight .w{color:#bbb}.highlight .mf{color:#f60}.highlight .mh{color:#f60}.highlight .mi{color:#f60}.highlight .mo{color:#f60}.highlight .sb{color:#c30}.highlight .sc{color:#c30}.highlight .sd{color:#c30;font-style:italic}.highlight .s2{color:#c30}.highlight .se{color:#c30}.highlight .sh{color:#c30}.highlight .si{color:#a00}.highlight .sx{color:#c30}.highlight .sr{color:#3aa}.highlight .s1{color:#c30}.highlight .ss{color:#fc3}.highlight .bp{color:#366}.highlight .vc{color:#033}.highlight .vg{color:#033}.highlight .vi{color:#033}.highlight .il{color:#f60}.css .o,.css .o+.nt,.css .nt+.nt{color:#999}.container{margin:0 auto;max-width:800px;width:80%}main,footer,.nav-container{display:block;margin:0 auto;max-width:800px;width:80%}.nav{box-shadow:0 2px 2px -2px rgba(0,0,0,0.2);overflow:auto}.nav-container{margin:1rem auto;position:relative;text-align:center}.nav-title{-webkit-transition:all 0.2s ease-out;-moz-transition:all 0.2s ease-out;transition:all 0.2s ease-out;color:#555;display:inline-block;margin:0;padding-right:.2rem}.nav-title:hover,.nav-title:focus{opacity:.6}.nav ul{list-style-type:none;margin:1rem 0 0;padding:0;text-align:center}.nav li{-webkit-transition:all 0.2s ease-out;-moz-transition:all 0.2s ease-out;transition:all 0.2s ease-out;color:#555;display:inline-block;opacity:.6;padding:0 2rem 0 0}.nav li:last-child{padding-right:0}.nav li:hover,.nav li:focus{opacity:1}.nav a{color:#555;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif}@media (min-width: 600px){.nav-container{text-align:left}.nav ul{bottom:0;position:absolute;right:0}}footer{font-family:Palatino,&quot;Palatino LT STD&quot;,&quot;Palatino Linotype&quot;,&quot;Book Antiqua&quot;,&quot;Georgia&quot;,serif;padding:2rem 0;text-align:center}footer span{color:#555;font-size:.8rem}.pagination{border-top:0.5px solid #e5e5e5;font-family:Palatino,&quot;Palatino LT STD&quot;,&quot;Palatino Linotype&quot;,&quot;Book Antiqua&quot;,&quot;Georgia&quot;,serif;padding-top:2rem;position:relative;text-align:center}.pagination span{color:#353535;font-size:1.1rem}.pagination .top{-webkit-transition:all 0.3s ease-out;-moz-transition:all 0.3s ease-out;transition:all 0.3s ease-out;color:#555;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif;font-size:1.1rem;opacity:.6}.pagination .top:hover{opacity:1}.pagination .arrow{-webkit-transition:all 0.3s ease-out;-moz-transition:all 0.3s ease-out;transition:all 0.3s ease-out;color:#555;position:absolute}.pagination .arrow:hover,.pagination .arrow:focus{opacity:.6;text-decoration:none}.pagination .left{left:0}.pagination .right{right:0}.catalogue-item{border-bottom:1px solid #e5e5e5;color:#555;display:block;padding:2rem 0}.catalogue-item:hover .catalogue-line,.catalogue-item:focus .catalogue-line{width:5rem}.catalogue-item:last-child{border:0}.catalogue-time{color:#aaa;font-family:Palatino,&quot;Palatino LT STD&quot;,&quot;Palatino Linotype&quot;,&quot;Book Antiqua&quot;,&quot;Georgia&quot;,serif;letter-spacing:.5px}.catalogue-title{color:#353535;display:block;font-family:&quot;Helvetica Neue&quot;,&quot;Segoe UI&quot;,Helvetica,Arial,sans-serif;font-size:2rem;font-weight:700;margin:.5rem 0}.catalogue-line{-webkit-transition:all 0.3s ease-out;-moz-transition:all 0.3s ease-out;transition:all 0.3s ease-out;border-top:0.2rem solid #353535;display:block;width:2rem}
html{font-family:sans-serif;-webkit-text-size-adjust:100%;-ms-text-size-adjust:100%}body{margin:0}footer,header,nav{display:block}a{background-color:transparent}a:active,a:hover{outline:0}strong{font-weight:700}h1{margin:.67em 0;font-size:2em}small{font-size:80%}img{border:0}svg:not(:root){overflow:hidden}button,input{margin:0;font:inherit;color:inherit}button{overflow:visible}button{text-transform:none}button,html input[type=button],input[type=reset],input[type=submit]{-webkit-appearance:button;cursor:pointer}button[disabled],html input[disabled]{cursor:default}button::-moz-focus-inner,input::-moz-focus-inner{padding:0;border:0}input{line-height:normal}@font-face{font-family:&#39;Glyphicons Halflings&#39;;src:url(../fonts/glyphicons-halflings-regular.eot);src:url(../fonts/glyphicons-halflings-regular.eot?#iefix) format(&#39;embedded-opentype&#39;),url(../fonts/glyphicons-halflings-regular.woff2) format(&#39;woff2&#39;),url(../fonts/glyphicons-halflings-regular.woff) format(&#39;woff&#39;),url(../fonts/glyphicons-halflings-regular.ttf) format(&#39;truetype&#39;),url(../fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular) format(&#39;svg&#39;)}*{-webkit-box-sizing:border-box;-moz-box-sizing:border-box;box-sizing:border-box}:after,:before{-webkit-box-sizing:border-box;-moz-box-sizing:border-box;box-sizing:border-box}html{font-size:10px;-webkit-tap-highlight-color:transparent}body{font-family:&quot;Libre Baskerville&quot;,&quot;Times New Roman&quot;,Times,serif;font-size:15px;line-height:1.42857143;color:#333;background-color:#fff}button,input{font-family:inherit;font-size:inherit;line-height:inherit}a{color:#337ab7;text-decoration:none}img{vertical-align:middle;margin:0 auto}[role=button]{cursor:pointer}.h1,.h2,.h3,h1,h2,h3{margin-top:20px;margin-bottom:10px}.h1 .small,.h1 small,.h2 .small,.h2 small,.h3 .small,.h3 small,h1 .small,h1 small,h2 .small,h2 small,h3 .small,h3 small{font-size:65%}.h4,.h5,.h6,h4,h5,h6{margin-top:10px;margin-bottom:10px}.h4 .small,.h4 small,.h5 .small,.h5 small,.h6 .small,.h6 small,h4 .small,h4 small,h5 .small,h5 small,h6 .small,h6 small{font-size:75%}.h1,h1{font-size:36px}.h2,h2{font-size:30px}.h3,h3{font-size:24px}.h4,h4{font-size:18px}.h5,h5{font-size:14px}.h6,h6{font-size:12px}p{margin:0 0 10px}.small,small{font-size:85%}.text-left{text-align:left}.text-right{text-align:right}.text-center{text-align:center}.text-success{color:#3c763d}a.text-success:focus,a.text-success:hover{color:#2b542c}.text-info{color:#31708f}a.text-info:focus,a.text-info:hover{color:#245269}.page-header{padding-bottom:9px;margin:40px 0 20px;border-bottom:1px solid #eee}.container{padding-right:15px;padding-left:15px;margin-right:auto;margin-left:auto}@media (min-width:768px){.container{width:750px}}@media (min-width:992px){.container{width:970px}}@media (min-width:1200px){.container{width:1170px}}.container-fluid{padding-right:15px;padding-left:15px;margin-right:auto;margin-left:auto}.row{margin-right:-15px;margin-left:-15px}.col-lg-1,.col-lg-10,.col-lg-11,.col-lg-12,.col-lg-2,.col-lg-3,.col-lg-4,.col-lg-5,.col-lg-6,.col-lg-7,.col-lg-8,.col-lg-9,.col-sm-1,.col-sm-10,.col-sm-11,.col-sm-12,.col-sm-2,.col-sm-3,.col-sm-4,.col-sm-5,.col-sm-6,.col-sm-7,.col-sm-8,.col-sm-9{position:relative;min-height:1px;padding-right:15px;padding-left:15px}table{background-color:transparent}.table{width:100%;max-width:100%;margin-bottom:20px}.table .table{background-color:#fff}table col[class*=col-]{position:static;display:table-column;float:none}table td[class*=col-]{position:static;display:table-cell;float:none}label{display:inline-block;max-width:100%;margin-bottom:5px;font-weight:700}input[type=search]{-webkit-box-sizing:border-box;-moz-box-sizing:border-box;box-sizing:border-box}input[type=checkbox],input[type=radio]{margin:4px 0 0;line-height:normal}input[type=file]{display:block}input[type=range]{display:block;width:100%}input[type=checkbox]:focus,input[type=file]:focus,input[type=radio]:focus{outline:5px auto -webkit-focus-ring-color;outline-offset:-2px}.form-control{display:block;width:100%;height:34px;padding:6px 12px;font-size:14px;line-height:1.42857143;color:#555;background-color:#fff;background-image:none;border:1px solid #ccc;border-radius:4px;-webkit-box-shadow:inset 0 1px 1px rgba(0,0,0,.075);box-shadow:inset 0 1px 1px rgba(0,0,0,.075);-webkit-transition:border-color ease-in-out .15s,-webkit-box-shadow ease-in-out .15s;-o-transition:border-color ease-in-out .15s,box-shadow ease-in-out .15s;transition:border-color ease-in-out .15s,box-shadow ease-in-out .15s}.form-control:focus{border-color:#66afe9;outline:0;-webkit-box-shadow:inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6);box-shadow:inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6)}.form-control::-moz-placeholder{color:#999;opacity:1}.form-control:-ms-input-placeholder{color:#999}.form-control::-webkit-input-placeholder{color:#999}.form-control::-ms-expand{background-color:transparent;border:0}.form-control[disabled],.form-control[readonly]{background-color:#eee;opacity:1}.form-control[disabled]{cursor:not-allowed}input[type=search]{-webkit-appearance:none}@media screen and (-webkit-min-device-pixel-ratio:0){input[type=date].form-control,input[type=datetime-local].form-control,input[type=month].form-control,input[type=time].form-control{line-height:34px}input[type=date].input-sm,input[type=datetime-local].input-sm,input[type=month].input-sm,input[type=time].input-sm{line-height:30px}input[type=date].input-lg,input[type=datetime-local].input-lg,input[type=month].input-lg,input[type=time].input-lg{line-height:46px}}input[type=checkbox].disabled,input[type=checkbox][disabled],input[type=radio].disabled,input[type=radio][disabled]{cursor:not-allowed}.input-sm{height:30px;padding:5px 10px;font-size:12px;line-height:1.5;border-radius:3px}.input-lg{height:46px;padding:10px 16px;font-size:18px;line-height:1.3333333;border-radius:6px}@media (min-width:768px){.form-inline .form-control{display:inline-block;width:auto;vertical-align:middle}.form-inline .control-label{margin-bottom:0;vertical-align:middle}}.btn{display:inline-block;padding:6px 12px;margin-bottom:0;font-size:14px;font-weight:400;line-height:1.42857143;text-align:center;white-space:nowrap;vertical-align:middle;-ms-touch-action:manipulation;touch-action:manipulation;cursor:pointer;-webkit-user-select:none;-moz-user-select:none;-ms-user-select:none;user-select:none;background-image:none;border:1px solid transparent;border-radius:4px}.btn.active.focus,.btn.active:focus,.btn.focus,.btn:active.focus,.btn:active:focus,.btn:focus{outline:5px auto -webkit-focus-ring-color;outline-offset:-2px}.btn.focus,.btn:focus,.btn:hover{color:#333;text-decoration:none}.btn.active,.btn:active{background-image:none;outline:0;-webkit-box-shadow:inset 0 3px 5px rgba(0,0,0,.125);box-shadow:inset 0 3px 5px rgba(0,0,0,.125)}.btn.disabled,.btn[disabled]{cursor:not-allowed;-webkit-box-shadow:none;box-shadow:none;opacity:.65}a.btn.disabled{pointer-events:none}.btn-default{color:#333;background-color:#fff;border-color:#ccc}.btn-default.focus,.btn-default:focus{color:#333;background-color:#e6e6e6;border-color:#8c8c8c}.btn-default:hover{color:#333;background-color:#e6e6e6;border-color:#adadad}.nav{padding-left:0;margin-bottom:0;list-style:none}.container-fluid:after,.container-fluid:before,.container:after,.container:before,.nav:after,.nav:before,.navbar-collapse:after,.navbar-collapse:before,.navbar-header:after,.navbar-header:before,.navbar:after,.navbar:before,.row:after,.row:before{display:table;content:&quot; &quot;}.container-fluid:after,.container:after,.nav:after,.navbar-collapse:after,.navbar-header:after,.navbar:after,.row:after{clear:both}#inputURL{width:100%}.bodyContainer{width:100%;position:relative;padding-left:0;padding-right:0}.footer{width:100%;height:60px;background-color:#f5f5f5;position:absolute;bottom:0}.container{width:auto;padding:0 15px}.container{width:100%;max-width:100%;text-align:center;display:flex;align-items:center;justify-content:center;flex-wrap:wrap;margin-top:0;margin-left:0}footer p{margin-bottom:0}.input-form{width:100%}.downloadForm{width:100%;height:75px}.navbar-header .topHeader{background:0 0}.navbar-header .container-fluid{padding-left:0}.adContainer{width:100%;margin-top:30px;height:150px;max-width:700px;overflow:hidden}.card{position:relative;display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-box-orient:vertical;-webkit-box-direction:normal;-ms-flex-direction:column;flex-direction:column;min-width:400px;word-wrap:break-word;background-color:#fff;background-clip:border-box;border:1px solid rgba(0,0,0,.125);border-radius:.25rem}.card-body{-webkit-box-flex:1;-ms-flex:1 1 auto;flex:1 1 auto;padding:1.25rem}.card-title{margin-bottom:.75rem;font-weight:bolder}@media only screen and (min-width:700px){.row.container-fluid .card.text-center{display:inline-block;width:37%}}@media only screen and (max-width:700px){.row.container-fluid{display:none}}@media only screen and (max-width:600px){.right-header{display:none}}.row.container-fluid{text-align:center;margin-top:100px}.footer-container{position:fixed;left:calc(50% - 84px);bottom:0}#sidebar,.hider *{display:none}.row *{font-size:16px;display:inline-block}body&gt;div.row.container-fluid.extra-info{margin-top:10px}.input-url{width:400px;font-size:18px}#container&gt;div{text-align:center}.submitBtn{padding:6px}.post-title{font-size:2rem!important}.imgContainer{width:100vw}main{width:100%;max-width:100%}.downloadForm{max-width:700px}.imgListing *{text-align:center;font-weight:bolder;font-size:17px}.lg-ad{width:calc(100% - 160px);margin:0 auto}@media only screen and (max-width:600px){#list2Ad{display:none}.container,.lg-ad{width:100%;height:90px!important}.col-lg-1{display:none}}.download-btn{padding:3px;color:#1e90ff;background-color:#fff;text-align:center;border:1px solid #ccc;border-radius:5px}@media (min-width:800px){h1{padding-right:100px}}@media (min-width:600px){main{width:calc(100% - 170px);padding:0;margin:0}.lg-ad{right:-170px!important}}
&lt;/style&gt;</b:widget-setting>
      </b:widget-settings>
      <b:includable id='main'>
  <!-- only display title if it's non-empty -->
  <b:if cond='data:title != &quot;&quot;'>
    <h2 class='title'><data:title/></h2>
  </b:if>
  <div class='widget-content'>
    <data:content/>
  </div>

  
</b:includable>
    </b:widget>
    <b:widget id='HTML1' locked='false' title='' type='HTML' version='1'>
      <b:widget-settings>
        <b:widget-setting name='content'>&lt;nav class=&quot;nav&quot; style=&#39;background: #E5583A;&#39;&gt;
			&lt;div class=&quot;nav-container&quot; style=&quot;width: 100%;max-width:100%;padding-left:20px;&quot;&gt;
				&lt;a href=&quot;/&quot;&gt;
					&lt;h1 class=&quot;nav-title&quot; style=&#39;font-size: 24px; color: #FFF;&#39;&gt;Freethumbnaildownloader.ml&lt;/h1&gt;
				&lt;/a&gt;
			&lt;/div&gt;
		&lt;/nav&gt;

&lt;main style=&#39;margin: 0 auto;&#39;&gt;

&lt;div class=&#39;bodyContainer&#39;&gt;
&lt;header style=&#39;margin-top: 20px; margin-bottom: 20px;&#39;&gt;
	&lt;p style=&#39;text-align: center;&#39;&gt;Youtube Thumbnail Downloader Supports All Youtube Videos Including &lt;b&gt;4K, 1080p, HD, HQ&lt;/b&gt;, etc.&lt;/p&gt;
&lt;/header&gt;

&lt;div class=&#39;container&#39;&gt;
&lt;table style=&#39;width: 100%;&#39;&gt;

&lt;form class=&#39;downloadForm&#39; onsubmit=&quot;event.preventDefault(); initDownloadLinks();&quot;&gt;
		&lt;tr&gt;&lt;td&gt;&lt;input aria-label=&#39;input URL &#39; class=&#39;form-control col-lg-6&#39; id=&#39;inputURL&#39; placeholder=&#39;Enter the youtube URL here&#39; type=&#39;text&#39;/&gt;&lt;/td&gt;&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;&lt;input type=&#39;submit&#39; class=&#39;btn btn-default&#39; id=&#39;submitButton&#39; type=&#39;button&#39; style=&#39;background: #25F982; font-weight: bold;&#39; value=&#39;Download YouTube Thumbnail&#39; /&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/form&gt;
&lt;/table&gt;
&lt;p style=&#39;text-align: center;margin:0 auto;max-width: 1000px;padding-top: 30px;padding-bottom: 30px;font-size: 16px;&#39;&gt;Freethumbnaildownloader.ml is a Free online tool, with the help of which you can download &lt;b&gt;Youtube Video Thumbnail&lt;/b&gt; in Different Sizes and Qualities. Just Paste your Youtube Video Link in the Input Box Given Below and press &quot;Download Youtube Thumbnail&quot;, and That&#39;s it.&lt;/p&gt;

&lt;div style=&quot;width:100%; margin-top: 20px;&quot;&gt; &lt;/div&gt;
&lt;div id=&quot;imgListing&quot;class=&#39;imgListing&#39; style=&quot;width:100%;left:0px&quot;&gt;
	&lt;div id=&#39;topListing&#39; style=&quot;display: none&quot;&gt;
		&lt;h5 class=&quot;right-click-info&quot;&gt;Right Click and click on &#39;Save Image As..&#39; to save the images.&lt;/h5&gt;
		&lt;h5 id=&#39;hdrestext&#39;&gt;HD Image (1280x720)&lt;/h5&gt;
		&lt;a id=&quot;hdreslink&quot; class=&quot;download-btn&quot;&gt;Download HD Youtube Thumbnail&lt;/a&gt;
		&lt;img id=&quot;maxres&quot; src=&quot;&quot; loading=&quot;eager&quot; /&gt;
		&lt;h5 id=&#39;sdrestext&#39;&gt;SD Image (640x480)&lt;/h5&gt;
		&lt;a id=&quot;sdreslink&quot; class=&quot;download-btn&quot;&gt;Download SD Youtube Thumbnail&lt;/a&gt;
		&lt;img id=&quot;sdres&quot; src=&quot;&quot; loading=&quot;auto&quot; /&gt;
	&lt;/div&gt;

	&lt;div id=&#39;bottomListing&#39; style=&quot;display: none&quot;&gt;
		&lt;h5 id=&#39;normalrestext&#39;&gt;Normal Image (480x360)&lt;/h5&gt;
		&lt;a id=&quot;hqreslink&quot; class=&quot;download-btn&quot;&gt;Download Normal Youtube Thumbnail (480x360)&lt;/a&gt;
		&lt;img id=&quot;hqres&quot; src=&quot;&quot; loading=&quot;lazy&quot; /&gt;
		&lt;div id=&#39;extraYTImg&#39;&gt;
		&lt;h5&gt;Normal Image (320x180)&lt;/h5&gt;
		&lt;a id=&quot;mqreslink&quot; class=&quot;download-btn&quot;&gt;Download Normal Youtube Thumbnail (320x180)&lt;/a&gt;
		&lt;img id=&quot;mqres&quot; src=&quot;&quot; loading=&quot;lazy&quot; /&gt;
		&lt;h5&gt;Normal Image (120x90)&lt;/h5&gt;
		&lt;a id=&quot;defreslink&quot; class=&quot;download-btn&quot;&gt;Download Normal Youtube Thumbnail (120x90)&lt;/a&gt;
		&lt;img id=&quot;defres&quot; src=&quot;&quot; loading=&quot;lazy&quot; /&gt;
	&lt;/div&gt;
&lt;/div&gt;


&lt;/div&gt;

&lt;!-- FOOTER TEXT --&gt;

&lt;div style=&#39;text-align: left;&#39;&gt;
&lt;h2&gt;How to Download HD Youtube Thumbnail&lt;/h2&gt;
&lt;ol&gt;
	&lt;li&gt;Copy the Youtube Video Link / URL from Youtube App or Website&lt;/li&gt;
	&lt;li&gt;Paste the Youtube video Link / URL in the Input Field Above.&lt;/li&gt;
	&lt;li&gt;Click on the &quot;Download Youtube Thumbnail&quot; Button.&lt;/li&gt;
	&lt;li&gt;You will get a list of all The Available Youtube Video Thumbnail Qualities, Which you can Choose From High Quality(HQ), High Definition (HD), 4K, 720p, 1080p Thumbnail, Low Quality and Medium Quality Youtube Thumbnails are also available.&lt;/li&gt;
	&lt;li&gt;Click on the Download Button, and Your Youtube Video Thumbnail will be Downloaded in your Device&#39;s Storage.&lt;/li&gt;
&lt;/ol&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;

&lt;/main&gt;</b:widget-setting>
      </b:widget-settings>
      <b:includable id='main'>
  <!-- only display title if it's non-empty -->
  <b:if cond='data:title != &quot;&quot;'>
    <h2 class='title'><data:title/></h2>
  </b:if>
  <div class='widget-content'>
    <data:content/>
  </div>

  
</b:includable>
    </b:widget>
  </b:section>
 </body>
</html>
