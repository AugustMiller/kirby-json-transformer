# Kirby JSON Transformer

The general goal here is to create a sort "presentation and transformation layer" for JSON a la [Fractal](http://fractal.thephpleague.com/), in Kirby.

It should accomplish a few things:

- Make it easy to translate data structures defined in Blueprints into arrays that can be passed to `json_encode` or Kirby's `response::json` methods.
- Expose "resources" or "transformers" to custom routes or [Content Representations](https://getkirby.com/docs/developer-guide/advanced/representations) with only a Blueprint's key
- Offer out-of-the-box filterability for whitelisted attributes
- Support an attribute blacklist for data that ought not be exposed
- Provide query metadata
- Have sane defaults or automatic behavior, but support extension when joins or more advanced/custom transformations are needed

Ultimately, passing data from the back- end to dynamic front-end components should be simpler— out-of-the-box, it requires a lot of boilerplate and basic attribute transformation (i.e. `$resource->field_name()->toString()`).

As mentioned above, the recent addition of [Content Representations](https://getkirby.com/docs/developer-guide/advanced/representations) are a great step, and the output of this plugin ough to be compatible with a basic `template.json.php` representation definition.

# Notes

I'll update this with ideas, until a time when past supporting work can be extracted and packaged into plugin.

- Review [`JsonSerializable` interface](https://secure.php.net/JsonSerializable) to see if we couldn't shim this in without a plugin, i.e. via Kirby's custom page models:
  ```php
  class MyTemplatePage extends Page implements JsonSerializable {
    public function jsonSerialize () { return [ /* ... */ ]; }
  }
  ```

:deciduous_tree:
