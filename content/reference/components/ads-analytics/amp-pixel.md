---
$title: "amp-pixel (Built-in)"
$order: 0
toc: true
---

<!---
Copyright 2015 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->



[TOC]

<table>
  <tr>
    <td class="col-fourty"><strong>Description</strong></td>
    <td>Can be used as a typical tracking pixel to count pageviews.</td>
  </tr>
  <tr>
    <td class="col-fourty"><strong><a href="https://www.ampproject.org/docs/guides/responsive/control_layout.html">Supported Layouts</a></strong></td>
    <td>fixed, nodisplay</td>
  </tr>
  <tr>
    <td class="col-fourty"><strong>Examples</strong></td>
    <td>See AMP By Example's <a href="https://ampbyexample.com/components/amp-pixel/">amp-pixel example</a>.</td>
  </tr>
</table>

## Behavior

The `amp-pixel` component behaves like a simple tracking pixel `img`. It takes a single URL, but provides variables that can be replaced by the component in the URL string when making the request. See the [substitutions](#substitutions) section for further details.

In this basic example, the `amp-pixel` issues a simple GET request to the given URL and ignores the result.

[sourcecode:html]
<amp-pixel src="https://foo.com/tracker/foo"
    layout="nodisplay"></amp-pixel>
[/sourcecode]

{% call callout('Note', type='note') %}
When processing AMP URLs in the referrer header of analytics requests, strip out or ignore the `usqp` parameter. This parameter is used by Google to trigger experiments for the Google AMP Cache.
{% endcall %}


## Attributes

##### src (required)

A simple URL to a remote endpoint that must be `https` protocol.

##### referrerpolicy (optional)

This attribute is similar to the `referrerpolicy` attribute on `<img>`, however `no-referrer` is the only accepted value. If `referrerpolicy=no-referrer` is specified, the `referrer` header is removed from the HTTP request.

[sourcecode:html]
<amp-pixel src="https://foo.com/tracker/foo"
    layout="nodisplay"
    referrerpolicy="no-referrer"></amp-pixel>
[/sourcecode]

##### allow-ssr-img (optional)

This attribute used in AMP4ADS creatives indicates that as part of post validation
transformation, an img element may be placed directly within the amp-pixel
element allowing the ping to be sent in parallel with AMP runtime fetch/execution.
Note that it means that any macros within the url will NOT be expanded so only
use if they are not present in the src.

##### common attributes

This element includes [common attributes](https://www.ampproject.org/docs/reference/common_attributes) extended to AMP components.

## Substitutions

The `amp-pixel` allows all standard URL variable substitutions.
See the [Substitutions Guide](https://github.com/ampproject/amphtml/blob/master/builtins/../spec/amp-var-substitutions.md) for more information.

In the following example, a request might be made to something like `https://foo.com/pixel?0.8390278471201` where the RANDOM value is randomly generated upon each impression.

[sourcecode:html]
<amp-pixel src="https://foo.com/pixel?RANDOM"
    layout="nodisplay"></amp-pixel>
[/sourcecode]

## Styling

`amp-pixel` should not be styled.

## Validation

See [amp-pixel rules](https://github.com/ampproject/amphtml/blob/master/validator/validator-main.protoascii) in the AMP validator specification.
