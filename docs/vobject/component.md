# vobject.component(name)

This is the base iCalendar object which consists of [`properties`](./property.md) and child `components`.

- `name` of the component. Ex: `VCALENDAR`, `VEVENT`

Usage:

```js
var component = vobject.component('VALARM');
component.pushProperty(vobject.property('ACTION', 'DISPLAY'));
component.toICS();
```

Example:

```
BEGIN:VCALENDAR
  PRODID:-//Google Inc//Google Calendar 70.9054//EN
  VERSION:2.0
  CALSCALE:GREGORIAN
  METHOD:REQUEST
  BEGIN:VEVENT
    ORGANIZER;CN=jeremy@sunrise.im:mailto:jeremy@sunrise.im
    ATTENDEE;CUTYPE=INDIVIDUAL;RSVP=TRUE;CN=Joey Dong;X-NUM-GUESTS=0:mailto:joey@sunrise.am
    SEQUENCE:1
    STATUS:CONFIRMED
    SUMMARY:Night Photowalk
    TRANSP:OPAQUE
  END:VEVENT
END:VCALENDAR
```

where `VCALENDAR` is an instance of a `vobject.component`, `PRODID, VERSION, CALSCALE` are properties of the component, and `VEVENT` is a sub-component.

-----------------------------------------------------------------------------------------

##### component.pushProperty(property)

- `property` to push onto the component. Expects a [`property`](./property.md) object

##### component.getProperties(name)

- `name` of the property to retrieve
- **returns** an array of [`property`](./property.md) objects set for `name`, `[]` by default

-----------------------------------------------------------------------------------------

##### component.setProperty(property)

- `property` to set as a unique property for the component. Expects a [`property`](./property.md) object

##### component.getProperty(name, index=0)

- `name` of the property to retrieve
- `index` of the property in cases of multiple instances of the property
- **returns** the [`property`](./property.md) object at the specified `name` and `index`, `undefined` by default

-----------------------------------------------------------------------------------------

##### component.pushComponent(childComponent)

- `childComponent` to be pushed onto the component. Expects a `component` object

##### component.getComponents(name)

- `name` of the subcomponent
- **returns** an array of subcomponents with specified name, `[]` by default

-----------------------------------------------------------------------------------------

##### component.toICSLines()

- **returns** rendered iCalendar representation of the component as an array of lines

##### component.toICS()

- **returns** rendered iCalendar string representation of the component

-----------------------------------------------------------------------------------------

##### component.escape [`RFC`](http://tools.ietf.org/html/rfc5545#section-3.3.11)
Escapes TEXT strings according to iCal spec. Characters to be escaped are `\n` (newline), `;` (semicolon), `:` (colon), and `,` (comma)

- `str` String to be escaped
- **returns** String escaped string

##### component.unescape(str) [`RFC`](http://tools.ietf.org/html/rfc5545#section-3.3.11)
Unescapes TEXT strings according to iCal spec. Characters to be unescaped are `\n` (newline), `;` (semicolon), `:` (colon), and `,` (comma)

- `str` String to be unescaped
- **returns** String unescaped string
