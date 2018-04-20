# \<mastodon-api\>

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/bgta/mastodont-api)

Mastodon API Polymer element.

## Demo

<!--
```
<custom-element-demo>
  <template>
    <link rel="import" href="my-element.html">
    <link rel="import" href="../other-element/other-element.html">
    <link rel="import" href="../iron-demo-helpers/demo-pages-shared-styles.html">
    <link rel="import" href="../iron-demo-helpers/demo-snippet.html">
    <link rel="import" href="../paper-card/paper-card.html">
    <link rel="import" href="../paper-checkbox/paper-checkbox.html">
    <link rel="import" href="../paper-input/paper-input.html">
    <link rel="import" href="../paper-button/paper-button.html">
    <link rel="import" href="mastodon-api.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
    <mastodon-api id="api" instance="mastodont.cat"></mastodon-api>

    <paper-card image="https://social.coop/packs/elephant-fren-d16fd77f9a9387e7d146b5f9d4dc1e7f.png">
    <h1>OAuth Information:</h2>
    <paper-input 
        label="Instance Domain" 
        id="instance"
        auto-validate pattern="^[a-zA-Z0-9]+([a-zA-Z0-9\-\.]+)?\.[a-zA-Z]{2,10}$" error-message="Please, fill a mastodon domain only">
    </paper-input>
    <paper-input 
        label="Client ID" 
        id="clientId">
    </paper-input>
    <paper-input 
        label="Redirect URL" 
        id="redirectUrl">
    </paper-input>
    <h2>Scopes:</h2>
    <ul>
        <li><paper-checkbox id="scope_read" checked>Read</paper-checkbox></li>
        <li><paper-checkbox id="scope_write">Write</paper-checkbox></li>
        <li><paper-checkbox id="scope_follow">Follow</paper-checkbox></li>
    </ul>
    <paper-button id="loginButton" raised>Authorize</paper-button>
    
    </paper-card>
    
    <script>
        document.addEventListener("DOMContentLoaded", function(event) { 
        function login() {
            var mastodonApi = document.getElementById('api');
            var clientId = document.getElementById('clientId').value;
            var redirectUrl = document.getElementById('redirectUrl').value;
            var scopes = [];
            if(document.getElementById('scope_read').checked)
            scopes.push('read');
            if(document.getElementById('scope_write').checked)
            scopes.push('write');
            if(document.getElementById('scope_follow').checked)
            scopes.push('follow');

            mastodonApi.clientId = clientId;
            mastodonApi.instance = document.getElementById('instance').value;
            mastodonApi.scopes = scopes;
            mastodonApi.redirectUrl = redirectUrl;
            mastodonApi.login();
        }

        document.getElementById('loginButton').addEventListener("click", login);
        document.getElementById('redirectUrl').value = document.location;
        });
        
    </script>
```

## Install the Polymer-CLI

First, make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.

## Viewing Your Element

```
$ polymer serve
```

## Running Tests

```
$ polymer test
```

Your application is already set up to be tested via [web-component-tester](https://github.com/Polymer/web-component-tester). Run `polymer test` to run your application's test suite locally.
