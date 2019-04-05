<center><h1>Jekyll-demos</h1></center>


<img src="https://raw.githubusercontent.com/eMous/__ResourceRepository/master/Jekyll_demos/2019/04/04/jekyll_demos_v1_intro.gif" style="border: solid gray 1px;     box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);">

Jekyll-demos is a static solution to show your `html/js/css` demos with Jekyll. And it's **not** a Jekyll plugin, so it means you are free to use it in Github Page.

<center><a href="https://emous.github.io/2019/04/05/MyDemoTool/">中文版本</a></center>

## Origin

The [jsfiddle.net](http://jsfiddle.net) which is the most elegant and free one I think is blocked in China, and the [gfwlist](https://github.com/gfwlist/gfwlist) project **does not** write it into the list means that All people in China can not directly or using an PAC-mode Shadowsocks setting view the embedded element of demos. So I decided to make a static one **JUST** using jekyll and no more http server except Github Page.

## Advantage

Compare to the online-service demo revealing tools like jsfiddle/codepen etc, it has a lot of innate advantage.

* It's totally free.
  It's a MIT-licensed open source project. 

* It's absolutly local and static.
  All your demos are orderly managed with the help of Jekyll. With the Github Page, you have nearly infinite storage that means as long as Github Page service is mantained, the static tool will power the whole demos of yours easily.

* It's quick to deploy.
  Totally you need only 3 steps:
  1. copy the `demoConf.yml` to your `_data` folder and setting your demos' repository path `demoBaseUrl`.
  2. copy the `list_demos.html` page to anywhere in your jekyll environment. And give it an front matters `id`.
  3. copy the tool setting to your `_config.yml`, make the `id` equals above set.

* It's also convenient to use. 
  You also need only 3 steps to show a demo.
  1. Add demo folder to any folder beneath the `demoBaseUrl`.
  2. Register the demo in `demoConf.yml`.
  3. ~~Include the js script.(You can do it once and for all with a layout.)~~
  4. Call a js function at anywhere you are going to show the demo.
    like this:
    ```html
    <script>demo_js.EmbedDemo("89798dasoid")</script>
    ```

* It supports multiple files in each demo.

## How does it work

Foremost, you write the path of each demo. 

When jekyll start to compile template, a file with Liquid Language will output all your demos orderly as its content. 

When js works, it make an http request to your site of that file and compare to the `demo_data_arr` which is output from jekyll's template and each demo's detail information. 

At last it generates the iframes dynamicly and use [CodeMirror](https://github.com/codemirror/CodeMirror/) editor to hightlight the code. 

![seq](https://raw.githubusercontent.com/eMous/__ResourceRepository/master/Jekyll_demos/2019/04/04/1554395612(1).jpg)
```seq

