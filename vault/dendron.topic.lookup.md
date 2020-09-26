---
id: a7c3a810-28c8-4b47-96a6-8156b1524af3
title: Lookup
desc: ''
updated: 1595952505038
created: 1595952505038
stub: false
---
# Lookup

To work with notes, Dendron uses  **lookups**. Lookups help you create, find, and organize your notes. You can watch the following video to see some of the things you can do with lookups.

<img style="" src="https://cdn.loom.com/sessions/thumbnails/a409a621763548d395e48c9d4380cbe7-1600813345789-with-play.gif"> </a>

## Notes

### Finding Notes

Below is an example of a simple two level hierarchy with notes on various [command line interface](https://en.wikipedia.org/wiki/Command-line_interface) commands. Use `Cmd+L` (we are going to use mac keybindings for this tutorial) to bring up the lookup and try some of the following queries.

```
- cli.tar
- cli.curl
- cli.dig
```
![](https://foundation-prod-assetspublic53c57cce-8cpvgjldwysl.s3-us-west-2.amazonaws.com/assets/images/lookup-cli.gif)

### Creating Notes

While we call it the `Lookup Bar`, you can also use it to create notes that don't exist. When you lookup for a note that hasn't been created, Dendron will create it for you. 

To try it yourself, bring up the lookup bar. Type `dendron.lookup.hello` and hit `Enter`.

#### Creating Special Notes

Dendron has builtin notion for certain notes with special naming conventions. Dendron has shortcuts to trigger the creation of such notes. 

((ref: [[dendron.topic.special-notes]]#journal note:#*))

((ref: [[dendron.topic.special-notes]]#scratch note:#*))

### Creating Notes with a Selection

If you have text highlighted while creating a new note with a lookup, the new note will be created using the text selected. How the text will be used depends on  the `dendron.defaultLookupCreateBehavior` setting.
- values: 
    - selectionExtract (default): create new note with text from the old note. remove text from the old note
    - selection2link: create new empty note and turn selection into a link referencing the old note

<a href="https://www.loom.com/share/61d754c1dca84b99b2786b2f89473566">
<img style="" src="https://cdn.loom.com/sessions/thumbnails/61d754c1dca84b99b2786b2f89473566-with-play.gif"> </a>


### Deleting Notes

To delete `dendron.lookup.hello`, use the `Cmd+Shift+D` shortcut on the note that you want to delete. Alternatively, you can also launch the `Command Bar` and type `Dendron: Delete Node` 

## Schemas

Dendron also provides lookup for [[schemas | dendron.topic.schema]]. To lookup a schema, use `> Dendron: Lookup Schema` or the `Cmd+Shift+L` (`Ctrl+Shift+L` on windows and linux) shortcut to bring up the schema lookup.

### Finding Schemas

The process for finding schemas using Dendron is the same as that for finding notes. One lookup to rule them all. 

![](https://foundation-prod-assetspublic53c57cce-8cpvgjldwysl.s3-us-west-2.amazonaws.com/assets/images/schema-lookup.gif)

### Creating Schemas

Just like with notes, if you enter the name of a schema that does not exist, Dendron will create it for you.

Specifically, Dendron will create `{value}.schema.yml` in your vault. At this point, you are free to edit the schema. After you're satisfied with the result, you'll need to run [[> Dendron: Reload Index| dendron.topic.commands]] for it to take affect. 

- NOTE: if you get an error after running `Reload Index`, it is most likely because your YAML is malformed. You can paste it in [yaml lint](http://www.yamllint.com/) to check that you are using the correct yaml syntax. 

![](https://foundation-prod-assetspublic53c57cce-8cpvgjldwysl.s3-us-west-2.amazonaws.com/assets/images/schema-create.gif)

### Deleting Schemas

The process for deleting schemas using Dendron is identical to deleting notes. 
