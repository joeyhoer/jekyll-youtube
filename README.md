# Introduction

This plugin adds a `{% youtube %}` Jekyll Liquid tag that generates a [YouTube](https://www.youtube.com) embed code.

# Installation

Move `youtube.rb` into the `_plugins` folder at the root of your Jekyll project.

# Syntax

```liquid
{% youtube video_id [width] [height] [data-attr:value]... %}
```

**Note:** If a `width` value is defined without a `height` value, a height have will be automatically defined based on the width using a `16:9` aspect ratio.

## Options

All [YouTube player parameters](https://developers.google.com/youtube/player_parameters#Parameters) are configurable with this extension.

Parameter         | Default      | Notes                                     
------------------|--------------|-------------------------------------------
autoplay          | 0            | autoplay                                  
cc_load_policy    | User Prefs   | Closed Captions                           
color             | red          | red/white (white disables modestbranding) 
controls          | 1            | Display video player controls             
disablekb         | 0            | Disable keyboard controls                 
enablejsapi       | 0            | Enable JavaScript API                     
end               | none         | Stop video at seconds                     
fs                | 1            | Display fullscreen button                 
hl                | none         | Player's interface language               
iv_load_policy    | 1            | 1/3 Display video annotations             
list              | none         | Read docs                                 
listType          | none         | Read docs                                 
loop              | 0            | Loop video                                
modestbranding    | 0            | 0/1 Hide YouTube logo                     
origin            | none         | Read docs                                 
playlist          | none         | List of video IDs                         
playsinline       | 0            | Play inline on iOS                        
rel               | 1            | Show related videos                       
showinfo          | 1            | Display video information                 
start             | none         | Start video at seconds                    
widget_referrer   | none         | Read docs                                 

**Note:** All default values are assigned by YouTube, not this plugin.

## Examples

```liquid
{% youtube dQw4w9WgXcQ %}
```

```liquid
{% youtube dQw4w9WgXcQ 600 rel:0 modestbranding:1 %}
```

## Global Configuration

Options may also be set globally by defining a `youtube` entry in the `_config.yml` file.

```
youtube:
  rel: 0
  modestbranding: 1
  iv_load_policy: 3
```

**Note:** Inline options overwrite the global options.

## Template

This extension allows you to define a template located at `_includes/youtube.html`, exposing `width`, `height`, `video_id` and `query_string` variables, to override the default output.

```liquid
<div class="video-embed">
  <iframe width="{{ width }}" height="{{ height }}" src="https://www.youtube.com/embed/{{ video_id }}{{ query_string }}" allowfullscreen></iframe>
</div>
```
