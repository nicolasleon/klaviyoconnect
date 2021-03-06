# Templating

## Add to List

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/update-profile">
    <label>Email</label><input type="email" name="email" />

    <!-- Add to the list -->
    <input type="hidden" name="list" value="FOO123">
    <input type="hidden" name="confirmOptIn" value="0" />

    <input type="submit" value="Submit"/>
</form>
```

## Add to List Using `Klaviyo List` Field Type

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/update-profile">
    <label>Email</label><input type="email" name="email" />

    <input type="hidden" name="list" value="{{ global.myKlaviyoList.id }}">

    <input type="hidden" name="confirmOptIn" value="0" />

    <input type="submit" value="Submit"/>
</form>
```

## Add to List Using `Klaviyo Lists` Field Type

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/update-profile">
    <label>Email</label><input type="email" name="email" />

    {% for id, name in global.myKlaviyoLists %}
    <input type="hidden" name="lists[]" value="{{ id }}">
    {% endfor %}

    <input type="hidden" name="confirmOptIn" value="0" />

    <input type="submit" value="Submit"/>
</form>
```

## Track Event

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/update-profile">

    <!-- Profile Details -->
    <label>Email</label><input type="email" name="email" />

    <!-- Event to track -->
    <input type="hidden" name="event[name]" value="Event Foo" />
    <input type="hidden" name="event[event_id]" value="a1b2c3" />
    <input type="hidden" name="event[value]" value="Foobar">
    <input type="hidden" name="event[extra][FooBar]" value="Foo Bar">

    <input type="submit" value="Submit"/>
</form>
```

## Track an Event and Add to a List

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/update-profile">

    <!-- Profile Details -->
    <label>Email</label><input type="email" name="email" />

    <!-- Add to the list -->
    <input type="hidden" name="list" value="FOO123">
    <input type="hidden" name="confirmOptIn" value="0" />

    <!-- Event to track -->
    <input type="hidden" name="event[name]" value="Event Foo" />
    <input type="hidden" name="event[event_id]" value="a1b2c3" />
    <input type="hidden" name="event[value]" value="Foobar">
    <input type="hidden" name="event[extra][FooBar]" value="Foo Bar">

    <input type="submit" value="Submit"/>
</form>
```

## Identify

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/identify">
    <label>Email</label><input type="email" name="email" />
    <input type="submit" value="Submit"/>
</form>
```

## Forward Requests

```
<form method="POST">
    <input type="hidden" name="action" value="klaviyoconnect/api/identify">
    <input type="hidden" name="forward" value="commerce/cart/update-cart">
    {{ redirectInput('commerce/cart') }}

    <label>Email</label><input type="email" name="email" />
    <input type="hidden" name="shippingAddressId" value="{{ address.id }}">
    <input type="hidden" name="sameAddress" value="1">

    <input type="submit" value="Submit"/>
</form>
```

