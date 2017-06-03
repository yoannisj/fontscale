# fontscale

Flexible type-scales with sass


## TODO

* Only accept string as $entry argument
* Implement 'fs-adjust-line-height'
* Refactor 'fs-font-size' to get font-size individually and clever-adjust
* Refactor 'fs-line-height' to get line-height individually and clever-adjust
* Refactor 'fs-values' to defer to 'fs-font-size' and 'fs-line-height'


**OR**

````scss
    
    $adjust: true;
    @if map-has-deep-key($typescale, $font, $name)
    {
        $entry: map-get-deep($typescale, $font, $name);
        $adjust: false;
    }

    @else
    {
        @if map-has-key($typescale, '*') {
            $entry: map-get-deep($tyepscale, '*', $name);
        }
        $entry: map-get($typescale, $name);
    }

    $fs: nth($entry, 1);
    @if $adjust {
        $fs: _fs-adjust-font-size($fs, $font);
    }

    $lh: if( length($entry) > 1, nth($entry, 2), _fs-calc-line-height($fs, $font));

    @if $adjust {
        $lh: _fs-adjust-line-height($lh, $font);
    }
````
