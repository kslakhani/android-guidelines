# Android Project Style Guidelines
The style guide is meant to keep the code consistent, clean and organized at a high level. It's mostly consist of the things that lint does't take care by default.

## Table of Contents
- [1. Project Guidelines](#1-project-guidelines)
  * [1.1 File Naming](#11-file-naming)
    + [1.1.1 Class Files](#111-class-files)
    + [1.1.2 Resource Files](#112-resource-files)
      - [1.1.2.1 Animation/Animator Files](#1121-animation-animator-files)
      - [1.1.2.1 Drawable Files](#1121-drawable-files)
      - [1.2.2.2 Layout Files](#1222-layout-files)
      - [1.1.2.3 Menu Files](#1123-menu-files)
      - [1.1.2.4 Values Files](#1124-values-files)
- [2. Code Guidelines](#2-code-guidelines)
  * [2.1 Java Language Rules](#21-java-language-rules)
  * [2.2 Java Style Rules](#22-java-style-rules)
    + [2.2.1 Class Organization](#221-class-organization)
    + [2.2.2 Meaningful Naming](#222-meaningful-naming)
    + [2.2.3 Field Naming](#223-field-naming)
      - [2.2.3.1 Constant Field Naming](#2231-constant-field-naming)
      - [2.2.3.2 View Field Naming](#2232-view-field-naming)
      - [2.2.3.3 Other Member Field Naming](#2233-other-member-field-naming)
    + [2.2.4 Method Naming](#224-method-naming)
    + [2.2.5 Method parameter ordering](#225-method-parameter-ordering)
    + [2.2.6 If-Statements](#226-if-statements)
      - [2.2.6.1 Inline if-clauses](#2261-inline-if-clauses)
      - [2.2.6.2 Nested if-conditions](#2262-nested-if-conditions)
      - [2.2.6.3 Ternary Operators](#2263-ternary-operators)
  * [2.3 XML Style Rules](#23-xml-style-rules)
    + [2.3.1 Resource naming](#231-resource-naming)
      - [2.3.2.1 IDs Naming](#2321-ids-naming)
      - [2.3.2.2 dimens.xml](#2322-dimensxml)
      - [2.3.2.3 Strings.xml](#2323-stringsxml)
      - [2.3.2.4 Styles.xml](#2324-stylesxml)
# 1. Project Guidelines


## 1.1 File Naming

### 1.1.1 Class Files

Class names are written in [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase).

Any classes extending an Android framework component should **always** end with the component name.
Example:
```
HomeActivity, LoginFragment, RateAppDialog, CountriesAdapter, AspectRatioFrameLayout, CircularImageView 
```


### 1.1.2 Resource Files
Resources file names are written in **snake_case**.

All resource names follow a simple convention.

&lt;WHERE&gt;\_&lt;WHAT&gt;\_&lt;DESCRIPTION&gt;\_&lt;SIZE&gt;



#### &lt;WHERE&gt;

Describe where it logically belongs in the app.

Example:

| Subclass                | &lt;WHERE&gt;    |
|------------------------ |------------------|
| HomeActivity            | home_            |
| LoginFragment           | login_           |
| RegisterFragment        | register_        |
| ArticalDetailFragment   | artical_detail_  |
| SelectRandomFragment    | select_random_   |

> For resources used in multiple screens use **all** as **&lt;WHERE&gt;**

#### &lt;WHAT&gt;

Indicate what the resource actually represents.

Example:
```
activity, fragment, item 
```

#### &lt;DESCRIPTION&gt;

Differentiate multiple elements in one screen.

#### &lt;SIZE&gt; (optional)

Either a precise size or size bucket. Optionally used for drawables and dimensions.

Example:

> `12dp`, `24dp`, `48dp`, `64dp`, `small`, `large`

#### 1.1.2.1 Drawable Files

For Drawables

**&lt;WHERE&gt;** indicate where the drawable will be used or `all` if the drawable is reused throughout the app.**&lt;WHAT&gt;** indicates what type of drawable is. **&lt;DESCRIPTION&gt;** indicate what the drawable is about. For example:

| Type         | &lt;WHAT&gt;  | Example                     |   
|--------------| --------------|-----------------------------|
| Selector     | selector_     | login_selector_envelope     |
| Shape        | shape_	       | all_shape_circle            |
| Vector       | vector_       | login_vector_lock           |
| Icon         | icon          | login_icon_envelope         |
| Image        | image_	       | login_image_background      |

Optionally you can add a **&lt;SIZE&gt;** or/and **&lt;COLOR&gt;** to diffrentiate same drawable of diffrent sizes or/and colors.

Example:
```
login_icon_envelope_24dp_white,  all_shape_button_primary, all_image_divider_grey
```

When creating selector state resources, they should be named using the corresponding suffix:

| State    | Suffix    | Example                             |
|----------|-----------|-------------------------------------|
| Normal   | _normal   |   all_shape_button_primary_normal   |
| Pressed  | _pressed  |   all_shape_button_primary_pressed  |
| Focused  | _focused  |   all_shape_button_primary_focused  |
| Disabled | _disabled |   all_shape_button_primary_disabled |
| Selected | _selected |   all_shape_button_primary_selected |


#### 1.2.2.2 Layout Files

When naming layout files, they should be named starting with the name of the Android Component that they have been created for. For example:

| Component        | Class Name      | Layout Name       |
|------------------|-----------------|-------------------|
| Activity         | MainActivity    | main_activity     |
| Fragment         | MainFragment    | main_fragment     |
| Dialog           | RateAppDialog   | rate_app_dialog   |
| Widget           | UserProfileView | user_profile_view |
| AdapterView Item | N/A             | user_item         |

**Note:** If you create a layout using the merge tag then the layout should be used for **&lt;WHAT&gt;**.

Not only does this approach makes it easy to find files in the directory that are related, but it really helps when needing to identify what corresponding class a layout file belongs to.


#### 1.1.2.3 Menu Files

For menu files we will use the same name as the layout file it belogns to.

Example: 
```
main_activity, main_fragment, login_activity, login_fragment
```

#### 1.1.2.4 Values Files

All resource file names should be plural.
Example:
```
attrs.xml, strings.xml, styles.xml, colors.xml, dimens.xml
```


# 2. Code Guidelines
## 2.1 Java Language Rules

## 2.2 Java Style Rules

### 2.2.1 Class Organization

The order you choose for the members and initializers of your class can have a great effect on learnability. So that new methods are not just habitually added to the end of the class.The following order could be used by spliting the class into section/regions like this:

1. Fields
    1. Constants
    2. Statics
    3. Dagger Injected fields
    4. Butterknife Binded fields
    5. Other Member fields
2. Static methods    
3. Constructors 
4. Lifecycle methods (should be ordered in the corresponding lifecycle order)
5. Override methods of Extended Class.
6. Overide methods of Interfaces Class.
7. Abstract methods declaration.
8. Butterknife Binded methods 
9. Any other instance methods
10. Interface declarations
11. Nested classes(static, then not-static)

Order of visiblity within each section/region should always follow this:

    static, public , protected, package private, private

you can create `sections` in a class to follow the order like this.

```java
/********* Constant Fields  ********/

private static final String TAG = "LoginFragment";

/********* Static Fields  ********/

private static int someStatic = 100; 

/********* Dagger Injected Fields  ********/

@Inject
LoginContract.Presenter presenter;

/********* Butterknife Binded Fields  ********/

@BindView(R.id.login_edit_text_password)
EditText editTextPassword;

/********* Member Fields  ********/

/********* Static Methods  ********/

/********* Constructors ********/

/********* Lifecycle Methods ********/

@Override
public void onCreate() {}

@Override
public void onResume() {}

@Override
public void onPause() {}

@Override
public void onDestroy() {}

/********* {extendedClassName} Inherited Methods ********/

/********* {extendedInterfaceName} Inherited Methods ********/

/********* Abstract Methods ********/

/********* Butterknife Binded Methods  ********/

/********* Member Methods  ********/

/********* Interfaces  ********/

/********* Nested Classes  ********/
// static, then non static
```



### 2.2.2 Meaningful Naming

When naming fields, methods and classes they should be meaningfull and to achieve that we can follow the flollwing points.

**Use intention revealing names:** The name of a variable, function, or class, should answer all the big questions. It
should tell you why it exists, what it does, and how it is used. If a name requires a comment,
then the name does not reveal its intent. 

**Use Pronounceable Names:** Names that are pronounceable avoids awkward conversations where you're trying to pronounce a badly named variable 

**Use Searchable Names:** Single-letter names and numeric constants have a particular problem in that they are not
easy to locate across a body of text. My personal preference is that single-letter names can ONLY be used as local variables inside short methods. The length of a name should correspond to the size of its scope

**Don't Use Hungarian Notation:**
Theses Encoding type or scope information into names simply adds an extra burden of deciphering and it also goes against the three points made above, so it should never be used!

### 2.2.3 Field Naming

#### 2.2.3.1 Constant Field Naming
Constants(static final) are written in ALL_CAPS_WITH_UNDERSCORES.

Many elements of the Android SDK such as `SharedPreferences`, `Bundle`, or `Intent` use a key-value pair approach so it's very likely that even for a small app you end up having to write a lot of String constants.

When using one of these components, you __must__ define the keys as a `static final` fields and they should be prefixed as indicated below.

| Element            | Field Name Prefix |
| -----------------  | ----------------- |
| SharedPreferences  | PREF_             |
| Bundle             | BUNDLE_           |
| Fragment Arguments | ARGUMENT_         |
| Intent Extra       | EXTRA_            |
| Intent Action      | ACTION_           |

Note that the arguments of a Fragment - `Fragment.getArguments()` - are also a Bundle. However, because this is a quite common use of Bundles, we define a different prefix for them.

Example:

```java
// Note the value of the field is the same as the name to avoid duplication issues
static final String PREF_EMAIL = "PREF_EMAIL";
static final String BUNDLE_AGE = "BUNDLE_AGE";
static final String ARGUMENT_USER_ID = "ARGUMENT_USER_ID";

// Intent-related items use full package name as value
static final String EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME";
static final String ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER";
```


#### 2.2.3.2 View Field Naming
When naming fields that reference views, the name of the view should be consistent with the [IDs Naming](#2321-ids-naming) IDs naming. Except you can skip **&lt;WHERE&gt;** in the name.

| View ID                 | View Field Name           |
|-------------------------|----------------------|
| login_edit_text_email   | editTextEmail        |
| login_edit_text_password| editTextPassowrd     |
| login_button_register   | buttonRegister       |
| login_linear_layout_form| linearLayoutForm     |



#### 2.2.3.3 Other Member Field Naming

All other member fields also start with a lower case letter.
For Example:

```java
private String username;
private int password;
private List<String> countryNames;
```



### 2.2.4 Method Naming

Java uses **camelCase** convention for method names. The Method name should have verb or verb phrase.

For example:

```
login() ,processAccount(), getUserDetail(), diaplayUserDetails()
```

### 2.2.5 Method parameter ordering

When defining methods, parameters should be ordered to the following convention:

```java
public Post loadPost(Context context, int postId);


public void loadPost(Context context, int postId, Callback callback);
```

**Context** parameters always go first and **Callback** parameters always go last.


### 2.2.6 If-Statements

#### 2.2.6.1 Inline if-clauses

Sometimes it makes sense to use a single line for if statements. For example:

```java
if (user == null) return false;
```

However, it only works for simple operations. Something like this would be better suited with braces:

```java
if (user == null) throw new IllegalArgumentExeption("Oops, user object is required.");
```

#### 2.2.6.2 Nested if-conditions

Where possible, if-conditions should be combined to avoid over-complicated nesting. For example:

Do:

```java
if (userSignedIn && userId != null) {

}

```
Try to avoid:

```java
if (userSignedIn) {
    if (userId != null) {

    }
}
```

This makes statements easier to read and removes the unnecessary extra lines from the nested clauses.

#### 2.2.6.3 Ternary Operators

Where appropriate, ternary operators can be used to simplify operations.
For example, this is easy to read:

```java
userStatusImage = signedIn ? R.drawable.ic_tick : R.drawable.ic_cross;
```

and takes up far fewer lines of code than this:

```java
if (signedIn) {
    userStatusImage = R.drawable.ic_tick;
} else {
    userStatusImage = R.drawable.ic_cross;
}
```

**Note:** There are some times when ternary operators should not be used. If the if-clause logic is complex or a large number of characters then a standard brace style should be used.

## 2.3 XML Style Rules

### 2.3.1 Resource naming

All resource names and IDs should be written using lowercase and underscores

#### 2.3.2.1 IDs Naming

For IDs, <WHERE> is the name of screen it belongs to. **&lt;WHAT&gt;** is the class name of the xml element it belongs to followed by an optional description to distinguish similar elements in one screen.

Here is the examples IDs name using this approach.

    login_edit_text_email, login_edit_text_password, login_button_register, login_linear_layout_form


#### 2.3.2.2 dimens.xml

Apps should only define a limited set of dimensions, which are constantly reused. This makes most dimensions **_all** by default.

Therefore you should mostly use:

**all\_&lt;WHAT&gt;\_&lt;DESCRIPTION&gt;**

and optionally use the screen specific variant:

**&lt;WHERE&gt;_&lt;WHAT&gt;\_&lt;DESCRIPTION&gt;**

where &lt;WHAT&gt; can be one of the followings.

| &lt;WHAT&gt;      | Usage                                           |
|-------------|-------------------------------------------------|
| width       | width in dp                                     |
| height      | height in dp                                    |
| size        | if width == height                              |
| margin      | margin in dp                                    |
| padding     | padding in dp                                   |
| elevation   | elevation in dp                                 |
| keyline     | absolute keyline measured from view edge in dp  |
| textsize    | size of text in sp                              |

You can take these dimensions as standard metrics for mostly used dimenions.

```xml
<dimen name="all_text_size_button">14sp</dimen>
<dimen name="all_text_size_caption">12sp</dimen>
<dimen name="all_text_size_body">14sp</dimen>
<dimen name="all_text_size_subheading">16sp</dimen>
<dimen name="all_text_size_title">20sp</dimen>
<dimen name="all_text_size_headline">24sp</dimen>
<dimen name="all_text_size_display1">34sp</dimen>
<dimen name="all_text_size_display2">45sp</dimen>
<dimen name="all_text_size_display3">56sp</dimen>

<dimen name="all_margin_micro">4dp</dimen>
<dimen name="all_margin_small">8dp</dimen>
<dimen name="all_margin_normal">16dp</dimen>
<dimen name="all_margin_medium">24dp</dimen>
<dimen name="all_margin_large">32dp</dimen>
<dimen name="all_margin_xlarge">48dp</dimen>
<dimen name="all_margin_huge">64dp</dimen>

<dimen name="all_padding_micro">4dp</dimen>
<dimen name="all_padding_small">8dp</dimen>
<dimen name="all_padding_normal">16dp</dimen>
<dimen name="all_padding_medium">24dp</dimen>
<dimen name="all_padding_large">32dp</dimen>
<dimen name="all_padding_xlarge">48dp</dimen>
<dimen name="all_padding_huge">64dp</dimen>

<dimen name="all_height_button_normal">36dp</dimen>
```

    

#### 2.3.2.3 Strings.xml

For name string resources. **&lt;WHERE&gt;** indicate where the string will be used or `all` if the string is reused throughout the app.**&lt;WHAT&gt;** indicates what type of string is. **&lt;DESCRIPTION&gt;** indicate what the strings is about. For example:

where &lt;WHAT&gt; can be one of the followings.

| &lt;WHAT&gt;      | Usage                                           |
|-------------|-------------------------------------------------|
| error       | An error message                                |
| message     | A regular information message                   |
| title       | A title, i.e. a activity title                  |
| action      | An action such as "Save" or "Discard"           |
| hint        | A hint text for Edittext                        |
| label       | A label for fields                              |

Here is example strings using this approach.

```xml
<string name="all_error_no_internet">No Internet Connection</string>

<string name="login_message_welcome">Welcome</string>
<string name="login_hint_email">Email Address</string>
<string name="login_hint_password">Password</string>
<string name="login_error_invalid_credentials">Invalid credentials</string>
<string name="login_error_email_required">Email address is required</string>
<string name="login_error_password_required">Password is required</string>

<string name="rate_app_title">Rate this app</string>
<string name="rate_app_message"></string>
<string name="rate_app_action_rate_now">Rate It Now</string>
<string name="rate_app_action_later">Later</string>
<string name="rate_app_action_no">No, Thanks</string>
```
## References
- https://github.com/bufferapp/android-guidelines
- https://jeroenmols.com/blog/2016/03/07/resourcenaming/
- https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship-ebook/dp/B001GSTOAM

   
