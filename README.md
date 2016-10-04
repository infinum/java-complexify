# java-complexify

Java port of Dan Palmers's [jquery.complexify.js](https://github.com/danpalmer/jquery.complexify.js/).

## Download

Use Gradle:

```gradle
repositories {
  jcenter()
}

dependencies {
  compile 'co.infinum:complexify-java:1.0.0'
}
```

## Usage

``` java

String password = ...

Complexify complexify = new Complexify();
complexify.checkComplexityOfPassword(password, new ComplexityListener() {
    @Override
    public void onSuccess(boolean isValid, double complexity) {
        // isValid is true if password is valid, false otherwise
        // complexity is number form range [0.0, 100.0] where greater number represents greater complexity
    }
});


```

There is also async method which does the same job but runs on another thread `complexify.checkComplexityOfPasswordAsync(...)`.


## Configuration

You can override the default configuration by using setters:

``` java

setBanMode(ComplexifyBanMode banMode) // use strict (don't allow substrings of banned passwords) or loose (only ban exact matches) comparisons for banned passwords. (default: ComplexifyBanMode.STRICT)

setStrengthScaleFactor(int strengthScaleFactor) // scale the required password strength (higher numbers require a more complex password) (default: 1)

setMinimumChars(int minimumChars) // the minimum acceptable password length (default: 8)

setBanList(String[] banList) // array of banned passwords (default: Generated from 500 worst passwords and 370 Banned Twitter lists found <a href="http://www.skullsecurity.org/wiki/index.php/Passwords">here</a>)

```

## License

This code is distributed under the WTFPL v2 licence.

