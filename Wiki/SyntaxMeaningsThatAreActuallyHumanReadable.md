### All up-to-date significant adblockers¹

* `##.` / `##` / `###`: Hides parts of a page.
* `||`: Blocks resources from domains or parts thereof from being loaded. For non-domain-specific resources, no pre-emption is needed at all.
* `@@`: Whitelists resources from specific URLs to make them load.
* `! ` / `# `: Marks the start of a comment that shall not be interpreted as an entry.
* `$thirdparty`: Ensures that resources from a domain is only blocked if you're not visiting the domain itself.
* `$domain=`: Ensures that resources from a domain is only blocked if you're visiting a specified website.
* `$generichide`: Prevents all non-domain-specific hiding entries from working on a website.
* `$script`: Blocks resources from domains or parts thereof from being loaded, but only if it is a script, e.g. a JavaScript runtime.
* `[href="text"]`: Looks for page elements whose values in the F12 filetree console contains such a value. The value can be either `href`, `id`, `class`, `type`, or several other things.
* `[href^="text"]`: Same as above, except it looks for anything whose value *begins* with the text.
* `[href*="text"]`: Same as above, except it looks for anything whose value contains the text anywhere within it.
* `:-abp-contains(text)`: Looks for page elements who contains such text within it.
* `:-abp-has(.element)`: Looks for page elements who contains such an element within it.
* `a` / `div` / `iframe` / `img` (among others): Looks for page elements that are specific element types, as seen in the F12 filetree console.
* `$csp`: Inserts additional *Content Security Policies* into the page.
* `~`: Means that an entry does *not* apply to a specific domain.
* `/\/\/\/` and similar: Text detections in RegEx format.
* `[Adblock Plus n.n]`: Used by Adblock Plus, AdBlock, and forks of them to determine if they should load the filterlist. Number is the intended minimum ABP version. `2.0` and `1.1` are most common; `3.1` is on the rise and can be used to block support for old forks. This has no effect on uBO or its forks.

### Nano Adblocker, uBlock Origin and AdGuard only:

* `:style`: Changes the CSS values of an element, in much the same way as what userstyle extensions like Stylish would've done.
* `{ }`: Same as above.
* `$badfilter`: Deactivates a resource-blocking entry, for cases where pre-empting it with `!` doesn't feel interesting enough.
* `:has-text`: Same as `:-abp-contains`.
* `:has`: Same as `:-abp-has`.
* `!#if`: Specifies that a section of entries only applies to specific platforms or extensions. Closed out by `!#endif`.
* `!#include`: Embeds another filterlist that is hosted on the same domain (with numerous restrictions).
* `$important`: Makes a resource-blocking entry take precedence over another whitelisting entry.

### Nano Adblocker and uBlock Origin only:

* `##+js`: Invokes a script that is embedded in those extensions, and usually using the script to modify a value on the site.
* `:xpath`: An entry written with the very advanced Xpath syntax.
* `127.0.0.1` / `0.0.0.0` / `::1`: Used by "*hosts*" system files to signify that network requests to such a domain shall be redirected to a local-only IP address, thus preventing it from loading. Nano and uBO treats it the same as `||`.

#### I can't remember what these ones do:

* `:-abp-properties`
* `##^`
* `$xmlhttprequest`
* `$redirect=noopjs`

# Particularly important usage notes

* `##.` / `##` / `###` entries can either be *generic*, in which they have no domains in front of them; or domain-specific, where they have one or more domains in front of them, separated by commas. Only Nano and uBO support wildcard asterisks (`*`) in such domains, while other adblockers do not.
* `||` entries do support asterisk wildcards, but only in the criteria text. Additionally, when using `$domain=`, domains are separated with vertical lines, since commas are instead used to stack multiple `$` values.
* `$generichide` entries must start with `@@||`.
* ABP is known to severely struggle with handling `:style` entries, to the point where having ABP try to load a list with such an entry will cause it to invalidate the list *and* all its entries.
* To make the text detection for `:-abp-contains` and `:has-text` case-insensitive, wrap the paranthesised text into `(/Example text/i)`.
* `127.0.0.1` / `0.0.0.0` / `::1` supports only whole domains, and it can not be narrowed down to subdomains or elements.
* The `"` in `[href="text"]` is optional, but *only* if the criteria text is only a single word.
* In `:-abp-has` and `:has`, it is not needed to pre-empt the criteria elements with `##`.
* `:style` and `{ }` does not allow to change `background-image` into a URL value.

¹ = Includes Nano Adblocker, uBlock Origin, AdGuard, Adblock Plus version ≥3.1, and AdBlock. It does **not** include Brave Browser, Slimjet, uBlock non-Origin, Adblock Plus for IE, Tracking Protection List, AdAway, or Blokada, whose syntax supports are considerably inferior to the above list.
