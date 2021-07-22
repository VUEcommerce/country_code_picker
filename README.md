FORKED to add bottom padding to listview when there's a keyboard open, will create a PR for the author

selection_dialog.dart
```
  child: ListView(
            padding: EdgeInsets.only(bottom: MediaQuery.of(context).viewInsets.bottom),
```


[![Pub](https://img.shields.io/pub/v/country_code_picker.svg)](https://pub.dartlang.org/packages/country_code_picker)

# country_code_picker

A flutter package for showing a country code selector.

It supports i18n.

<img src="https://raw.githubusercontent.com/Salvatore-Giordano/CountryCodePicker/master/screenshots/screen1.png" width="240"/>
<img src="https://raw.githubusercontent.com/Salvatore-Giordano/CountryCodePicker/master/screenshots/screen2.png" width="240"/>

## Usage

Just put the component in your application setting the onChanged callback.

```dart

@override
 Widget build(BuildContext context) => new Scaffold(
     body: Center(
       child: CountryCodePicker(
         onChanged: print,
         // Initial selection and favorite can be one of code ('IT') OR dial_code('+39')
         initialSelection: 'IT',
         favorite: ['+39','FR'],
         // optional. Shows only country name and flag
         showCountryOnly: false,
         // optional. Shows only country name and flag when popup is closed.
         showOnlyCountryWhenClosed: false,
         // optional. aligns the flag and the Text left
         alignLeft: false,
       ),
     ),
 );

```

Example:

```dart

void _onCountryChange(CountryCode countryCode) {
    //TODO : manipulate the selected country code here
    print("New Country selected: " + countryCode.toString());
  }

```

### i18n

Just add the `CountryLocalizations.delegate` in the list of your app delegates

```dart
 return new MaterialApp(
      supportedLocales: [
        Locale('en'),
        Locale('it'),
        Locale('fr'),
        Locale('es'),
      ],
      localizationsDelegates: [
        CountryLocalizations.delegate,
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
```

## Customization

Here is a list of properties available to customize your widget:

| Name | Type | Description |
|-----|-----|------|
|onChanged| ValueChanged<CountryCode> | callback invoked when the selection changes |
|onInit| ValueChanged<CountryCode> | callback invoked during initialization of the widget |
|initialSelection| String | used to set the initial selected value |
|favorite| List<String> | used to populate the favorite country list |
|textStyle| TextStyle | TextStyle applied to the widget button |
|padding| EdgeInsetsGeometry | the padding applied to the button |
|showCountryOnly| bool | true if you want to see only the countries in the selection dialog |
|searchDecoration| InputDecoration | decoration applied to the TextField search widget |
|searchStyle| TextStyle | style applied to the TextField search widget text |
|emptySearchBuilder| WidgetBuilder | use this to customize the widget used when the search returns 0 elements |
|builder| Function(CountryCode) | use this to build a custom widget instead of the default FlatButton |
|enabled| bool | set to false to disable the widget |
|textOverflow| TextOverflow | the button text overflow behaviour |
|dialogSize| Size | the size of the selection dialog |
|countryFilter| List<String> | uses a list of strings to filter a sublist of countries |
|showOnlyCountryWhenClosed| bool | if true it'll show only the country |
|alignLeft| bool | aligns the flag and the Text to the left |
|showFlag| bool | shows the flag everywhere |
|showFlagMain| bool | shows the flag only when closed |
|showFlagDialog| bool | shows the flag only in dialog |
|flagWidth| double | the width of the flags |
|comparator| Comparator<CountryCode> | use this to sort the countries in the selection dialog |
|hideSearch| bool | if true the search feature will be disabled |

## Contributions

Contributions of any kind are more than welcome! Feel free to fork and improve country_code_picker in any way you want, make a pull request, or open an issue.
