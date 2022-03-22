Useful IntelliJ Live Templates
===
This repository contains some Live Templates for IntelliJ which I frequently use.
The collection will likely get expanded over time.

## Importing

The best way to import these templates is by dragging the individual files in your configuration folder.

On Windows, templates are located in the following directory:

`%APPDATA%\JetBrains\<CURRENT_VERSION>\templates`

Respectively, on Mac:

`~/Library/Application Support/JetBrains/<CURRENT_VERSION>/templates`

Restart your IDE after import.

You can adjust, rename and disable/enable any templates however you like after you've imported the files.

## Templates

### Angular

#### ngit

Basic *ngFor with index.

Has reasonable defaults for tag name, var name and index var name.

```
<$TAG_NAME$ *ngFor="let $VAR$ of $LIST$; index as $INDEX$">$END$</$TAG_NAME$>
```

#### ngsc

Angular component with added `destroyed$`-Subject for use with `takeUntil`.

Class and selector names are derived from the file name as default.

```
import {Component, OnInit, OnDestroy} from "@angular/core";
import {Subject} from "rxjs";

@Component({
    selector: "$PREFIX$-$SELECTOR$",
    templateUrl: "./$SELECTOR$.component.html",
    styleUrls: ["./$SELECTOR$.component.scss"]
})
export class $NAME$Component implements OnInit, OnDestroy {
  destroyed$: Subject<void> = new Subject<void>();
  
  ngOnInit(): void {
  }
  
  ngOnDestroy(): void {
    this.destroyed$.next();
    this.destroyed$.complete();
  }
}
```

### CSS

#### bpm

Mobile breakpoint.

```
@media only screen and (max-width: $BREAKPOINT$) {
$END$
}
```

#### fcol

Flex column.

```
display: flex;
flex-direction: column;
```

#### frow

Flex row.

```
display: flex;
flex-direction: row;
```

#### gfnt

Local import of a Google Font as TTF, with FOUT.

For a "Regular" font it should suffice to enter the font name, as the rest is derived.

```
@font-face {
    font-family: "$FONT_NAME$";
    font-style: $FONT_STYLE$;
    font-weight: $FONT_WEIGHT$;
    font-display: swap;
    src: local("$FONT_NAME$$ADDITIVE$"), local("$FONT_NAME_COLLAPSED$-$ADDITIVE_COLLAPSED$"), url("$PATH$$FONT_NAME_COLLAPSED$-$ADDITIVE_COLLAPSED$.ttf") format("truetype");
}
```

#### hb

Classic CSS setup.

``` 
html, body {
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
}
```

#### nfc

"Not first child" selector.

```
$SELECTOR$:not(:first-child) {
$END$
}
```

#### nlc

"Not last child" selector.

```
$SELECTOR$:not(:last-child) {
$END$
}
```

#### tcub 

Cubic bezier transition with reasonable defaults.

```
transition: $PROP$ $TIME$ cubic-bezier($PARAM_1$, $PARAM_2$, $PARAM_3$, $PARAM_4$); 
```

#### tease 

Ease transition with a reasonable default time.

``` 
transition: $PROP$ $TIME$ ease;
```

### GWT

#### jsobj

Final JavaScriptObject class with a default "constructor".

``` 
import com.google.gwt.core.client.JavaScriptObject;

@SuppressWarnings("ProtectedMemberInFinalClass")
public final class $CLASS_NAME$ extends JavaScriptObject {
    protected $CLASS_NAME$() {} // Required by GWT.

    $END$
    
    /**
     * Replacement constructor.
     * Creates a new native {@link $CLASS_NAME$}.
     * @return The new instance.
     */
    public static native $CLASS_NAME$ create(
        
    )/*-{
        return {
            
        };    
    }-*/;
}
```

#### jsp

JavaScript property for a JavaScriptObject class.

Names are derived, you only need to enter the type and name once.

```
public native $TYPE$ get$NAME$()/*-{
    return this.$NAME_LC$;
}-*/;

public native void set$NAME$($TYPE$ $NAME_LC$)/*-{
    this.$NAME_LC$ = $NAME_LC$;
}-*/;
```

#### jspb

JavaScript boolean property for a JavaScriptObject class.

Names are derived, you only need to enter the name once.

``` 
public native boolean is$NAME$()/*-{
    return this.$NAME_LC$;
}-*/;

public native void set$NAME$(boolean $NAME_LC$)/*-{
    this.$NAME_LC$ = $NAME_LC$;
}-*/;
```

#### jspf

Final JavaScript property for a JavaScriptObject class.

Names are derived, you only need to enter the type and name once.

```
public final native $TYPE$ get$NAME$()/*-{
    return this.$NAME_LC$;
}-*/;

public final native void set$NAME$($TYPE$ $NAME_LC$)/*-{
    this.$NAME_LC$ = $NAME_LC$;
}-*/;
```

#### jspfb

Final JavaScript boolean property for a JavaScriptObject class.

Names are derived, you only need to enter the name once.

``` 
public final native boolean is$NAME$()/*-{
    return this.$NAME_LC$;
}-*/;

public final native void set$NAME$(boolean $NAME_LC$)/*-{
    this.$NAME_LC$ = $NAME_LC$;
}-*/;
```

### Java

#### sing

Basic singleton class. Name is derived from the file name.

```
public class $FILE_NAME$ {
    private static $FILE_NAME$ instance;

    private $FILE_NAME$() {}

    $END$

    public static $FILE_NAME$ get() {
        if (instance == null) {
            instance = new $FILE_NAME$();
        }
        return instance;
    }
}
```

### JavaScript

#### clof

Better `console.log()` template. File name is supplied automatically.

```
console.log("[$VALUE$] in [$FILENAME$]", $VALUE$);
```

#### clog

Better `console.log()` template.

```
console.log("[$VALUE$]", $VALUE$);
```

### SCSS

#### smix

Some evergreen default mixins every web app can make use of.

``` 
@mixin flex-row($center-horizontal: false, $center-vertical: false) {
  display: flex;
  flex-direction: row;

  @if $center-horizontal {
    justify-content: center;
  } @else {
    justify-content: flex-start;
  }

  @if $center-vertical {
    align-items: center;
  } @else {
    align-items: flex-start;
  }
}

@mixin flex-column($center-horizontal: false, $center-vertical: false) {
  display: flex;
  flex-direction: column;

  @if $center-horizontal {
    align-items: center;
  } @else {
    align-items: flex-start;
  }

  @if $center-vertical {
    justify-content: center;
  } @else {
    justify-content: flex-start;
  }
}

@mixin unselectable {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
```

### TypeScript

#### sing

Basic singleton class. Name is derived from the file name.

```
export class $FILE_NAME$ {
    private static instance: $FILE_NAME$;

    private constructor() {}
    
    $END$
    
    public static get(): $FILE_NAME$ {
        if (!$FILE_NAME$.instance) {
            $FILE_NAME$.instance = new $FILE_NAME$();
        }
        
        return $FILE_NAME$.instance;
    }
}
```


## License and Contributing

By contributing, you agree that your contributions will be licensed under the repository's [Unlicense](./LICENSE).
