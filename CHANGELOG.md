# Change Log

**0.9.0**
- Improvements to RollbarHandler logging handler. It now:
  - extracts more information out of each record (i.e. metadata like pathname and creation time)
  - uses the format string, with arguments not yet replaced, as the main message body. This will result in much better grouping in Rollbar.

Note about upgrading from 0.8.x: unless you are using RollbarHandler, there are no breaking changes. If you are using RolbarHandler, then this will change the way your data appears in Rollbar (to the better, in our opinion).

**0.8.3**
- Provide a way to blacklist types from being repr()'d while gathering local variables.

**0.8.2**
- Fix uncaught ImproperlyConfigured exception when importing Rollbar in a Django REST Framework environment without a settings module loaded ([#28](https://github.com/rollbar/pyrollbar/pull/28))

**0.8.1**
- Only attempt local variable extraction if traceback frames are of the correct type, print a warning otherwise
- Fix JSON request param extraction for Werkzeug requests (Pyramid, Flask, etc)

**0.8.0**
- Local variables collection now enabled by default.
- Fixed scrubbing for utf8 param names.

**0.7.6**
- Added local variables for all in-project frames and the last frame.

**0.7.5**
- Initial support for sending args and kwargs for traceback frames.
- Optimization to send the access token in a header.

**0.7.4**
- Level kwarg added to `rollbar.report_exc_info()` ([#22](https://github.com/rollbar/pyrollbar/pull/22))

**0.7.3**
- Added in an optional `endpoint` parameter to `search_items()`.

**0.7.2**
- Fix for scrubbing werkzeug json bodies ([#20](https://github.com/rollbar/pyrollbar/pull/20))

**0.7.1**
- Support scrubbing for werkzeug json bodies ([#19](https://github.com/rollbar/pyrollbar/pull/19))

**0.7.0**
- Python 3 support
- Now support extracting data from Django REST framework requests
- New `enabled` configuration setting

**0.6.2**
- Fixed json request data formatting for reports in Bottle requests
- Now send json request data for Django and Pyramid apps
- Set framework and request context properly for all reports in Flask and Bottle apps

**0.6.1**
- Added Django, Pyramid, Flask and Bottle support for default contexts.

**0.6.0**
- `report_message()` now returns the UUID of the reported occurrence.

**0.5.14**
- Fix bug with non-JSON post data in Flask
- Add slightly better integration with Flask. See [rollbar-flask-example](https://github.com/rollbar/rollbar-flask-example) for example usage.

**0.5.13**
- Collect JSON post data in Flask when mimetype is `application/json`

**0.5.12**
- Add sys.argv to server data

**0.5.11**
- Don't report bottle.BaseResponse exceptions in the bottle plugin

**0.5.10**
- Added `code_version` configuration setting
- Added support for bottle request objects

**0.5.9**
- Added a command line interface for reporting messages to Rollbar

**0.5.8**
- Added `allow_logging_basic_config` config flag for compatability with Flask. If using Flask, set to False.

**0.5.7**
- Added `exception_level_filters` configuration setting to customize the level that specific exceptions are reported as.

**0.5.6**
- First argument to `rollbar.report_exc_info()` is now optional. You can now call it with no arguments from within an `except` block, and it will behave is if you had called like `rollbar.report_exc_info(sys.exc_info())`

**0.5.5**
- Support for ignoring exceptions by setting `exc._rollbar_ignore = True`. Such exceptions reported through rollbar.report_exc_info() -- which is used under the hood in the Django and Pyramid middlewares -- will be ignored instead of reported.

**0.5.4**
- Django: catch exceptions when patching the debugview, for better support for django 1.3.

**0.5.3**
- Fixed bug when reporting messages without a request object

**0.5.2**
- Fixed bug where django debug page can get patched twice

**0.5.1**
- Catching possible malformed API responses

**0.5.0**
- Rename to rollbar

**0.4.1**
- report_exc_info() now takes two additional named args: `extra_data` and `payload_data`, like report_message().
- on 429 response (over rate limit), log a warning but don't parse and print an exception.

**0.3.2**
- Added new default scrub fields

**0.3.1**
- Fixed pypi package

**0.3.0**
- Merge django-ratchet and pyramid_ratchet into pyratchet
- Add ability to write to a ratchet-agent log file

**0.2.0**
- Add "person" support

**0.1.14**
- Added payload_data arg to report_message()

**0.1.13**
- Added extra_data arg to report_message()

**0.1.12**
- Use custom JSON encoder to skip objects that can't be encoded.
- Bump default timeout from 1 to 3 seconds.

**0.1.11**
- Sensitive params now scrubbed out of POST. Param name list is customizable via the `scrub_fields` config option.

**0.1.10**
- Add support for Tornado request objects (`tornado.httpserver.HTTPRequest`)

**0.1.9**
- Fix support for Pyramid request objects

**0.1.8**
- Add support for Django request objects

