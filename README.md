InPlayer Paywall v2
=======================

[inplayer.com](https://inplayer.com)

## Installation

Install the package from [npm](https://www.npmjs.com/package/@inplayer-org/paywall) and import it in your project.

```bash
npm install --save @inplayer-org/paywall
```

Alternately include the script like so:

```
<script src="https://assets.inplayer.com/paywall/0.1.0/paywall.min.js"></script>
```

## Loading an asset with an ID

```
// Basic example  InPlayerPaywall(merchantUUID, [Object{id, ...options}])

<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
        id: 40112
      }
     ]
)
</script>
```

## Loading an asset with external ID

```
<script>
  // This id is an external one, the type has to be specified as well.
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
         external: {
            type: 'brightcove',
            id: 5784466086001,
         },
      },
     ]
)
</script>
```
## Main available ASSET options
 - noPreview
 - brandingId

Example:

```
<script>
  // No preview option and branding option
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
        id: 40112,
        noPreview: true, // Default is false - the preview wont show if enabled
        brandingId: "51424", // Enables usage of branding different than the default one
      }
     ]
)
</script>
```


## Additional ASSET options
- Additional CSS/JS scripts import
- Additional Query Params for asset initialization

Example:
```
// Importing scripts (CSS/JS)

<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
        id: 40112,
        noPreview: true, // Default is false - the preview wont show if enabled
        brandingId: "51424", // Enables usage of branding different than the default one
        options: {
           scripts: [
             {  src: 'https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js',
                type: 'script',
                id: 'my-custom-id',
                async: false //whether the script should be loaded async (default=true)
             },
             {
                href: 'https://ajax.googleapis.com/jquery.mobile.min.css',
                type: 'css',
             }             
           ],
        }
      }
     ]
)
</script>

// Adding Query Params in the request for the asset
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
        id: 40112,
        noPreview: true, // Default is false - the preview wont show if enabled
        brandingId: "51424", // Enables usage of branding different than the default one
        options: {
          params: {
            language: 'en',
            myParam: 'any value'
          }
        }
      }
     ]
)
</script>
```

## Additional Paywall options
- default paywall language
- show/hide the user menu
- show/hide the logo in the modal

Example:
```
<script>
  // InplayerPaywall(merchant UUID, [Object{id, ...opts}], {...opts})
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
         id: 1234
      },
     ],
     {
       language: 'EN',//sets the default language
       hideUserMenu: true, // hides the user menu dropdown (default=false)
       hideLogo: true, //hides the logo in the modal header (default=false)
     }
)
</script>
```

## Standalone Paywall functions
 - setLanguage
 - setLoginScreen
 - setRegisterScreen
 - setMyAccountScreen
 - showPaywall
 - logoutUser

Example:
```
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
     [
      {
         id: 1234
      },
     ],
  );

  paywall.setLanguage('EN'); //sets the active paywall language
  paywall.setLoginScreen(); //displays the paywall login screen
  paywall.logoutUser(); //logs out the logged in user
  paywall.setRegisterScreen(); //displays the register screen
  paywall.setMyAccountScreen(); //displays the my account screen (the user needs to be authenticated)
  paywall.showPaywall(); //displays the paywall (same as when you would click on the buy button)
</script>
```
