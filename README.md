# purescript-dom

[![Latest release](http://img.shields.io/bower/v/purescript-dom.svg)](https://github.com/purescript-contrib/purescript-dom/releases)
[![Build Status](https://travis-ci.org/purescript-contrib/purescript-dom.svg?branch=master)](https://travis-ci.org/purescript-contrib/purescript-dom)
[![Maintainer: garyb](https://img.shields.io/badge/maintainer-garyb-lightgrey.svg)](http://github.com/garyb)

Type definitions, low level interface implementations, and standard effect type for use while interacting with the DOM.

## Installation

```
bower install purescript-dom
```

## Introduction

`purescript-dom` is intended to provide a common base for projects that need to talk to or about the DOM.

The API isn't primarily intended for "human consumption", but instead aims to provide functions and types that match up with the interfaces described in the [DOM4](http://www.w3.org/TR/dom/) and [HTML5](http://www.w3.org/TR/html5/) specifications, with a minimal amount of additional opinion as to how they should be implemented in PureScript.

This consists of:
- `foreign data` types for the various interfaces described.
- Functions that read `Foreign` typed values (and `IsForeign` instances) for foreign types.
- No classes or other niceties to aid with subtyping relationships. However, coercions are provided from subtypes to their supertypes. For example, from `DOM.Node.Types`,  [`elementToNode`](https://github.com/purescript-contrib/purescript-dom/blob/master/docs/DOM/Node/Types.md#elementtonode).
- Functions that can mutate the DOM, or that don't always return the same value, or return a value that may be mutated at a distance use `Eff` with the `DOM` effect
- Enumeration values are provided as ADTs, but with an option to read the raw value too. For example, from `DOM.Node.Node`, [`nodeType`](https://github.com/purescript-contrib/purescript-dom/blob/master/docs/DOM/Node/Node.md#nodetype) and [`nodeTypeIndex`](https://github.com/purescript-contrib/purescript-dom/blob/master/docs/DOM/Node/Node.md#nodetypeindex).

## Module structure

Interfaces from DOM4 are grouped under `DOM.Node` and interfaces from HTML5 are grouped under `DOM.HTML`, aside from event-related things which are grouped under `DOM.Events`. Additionally there are a few other useful `DOM` interfaces such as the [File](http://www.w3.org/TR/FileAPI/) and [XMLHttpRequest2](http://www.w3.org/TR/XMLHttpRequest2/) that have their own submodules.

In each submodule there is a `.Types` which should enumerate `foreign` data types for the interfaces within and the coercions and `Foreign`-reading functions that go with them. After that each interface should have its own submodule - so for example, `Element` is provided in `DOM.Node.Types` and the functions from the `Element` API are defined in `DOM.Node.Element`. Enumeration types such as `NodeType` also get their own modules, such as `DOM.Node.NodeType`.

## Non-standards compliant interfaces

Currently we're choosing not to implement deprecated or non-standard interfaces even if they are commonly available. The `innerHTML` property of  `Element` and `keyCode`/`charCode` of `KeyboardEvent` being examples of this. Ideally this module will only provide types and functions that "everyone" can agree on. This also means new parts of the specifications that are currently not widely available may also be omitted for the time being, however this only applies to the API implementation, types for new interfaces will be included as needed. 

## Module documentation

- [DOM](docs/DOM.md)
- [DOM.Event.Event](docs/DOM/Event/Event.md)
- [DOM.Event.EventPhase](docs/DOM/Event/EventPhase.md)
- [DOM.Event.EventTarget](docs/DOM/Event/EventTarget.md)
- [DOM.Event.EventTypes](docs/DOM/Event/EventTypes.md)
- [DOM.Event.Types](docs/DOM/Event/Types.md)
- [DOM.File.Types](docs/DOM/File/Types.md)
- [DOM.HTML](docs/DOM/HTML.md)
- [DOM.HTML.Document](docs/DOM/HTML/Document.md)
- [DOM.HTML.Types](docs/DOM/HTML/Types.md)
- [DOM.HTML.Window](docs/DOM/HTML/Window.md)
- [DOM.Node.ChildNode](docs/DOM/Node/ChildNode.md)
- [DOM.Node.Document](docs/DOM/Node/Document.md)
- [DOM.Node.DocumentType](docs/DOM/Node/DocumentType.md)
- [DOM.Node.Element](docs/DOM/Node/Element.md)
- [DOM.Node.HTMLCollection](docs/DOM/Node/HTMLCollection.md)
- [DOM.Node.Node](docs/DOM/Node/Node.md)
- [DOM.Node.NodeList](docs/DOM/Node/NodeList.md)
- [DOM.Node.NodeType](docs/DOM/Node/NodeType.md)
- [DOM.Node.NonDocumentTypeChildNode](docs/DOM/Node/NonDocumentTypeChildNode.md)
- [DOM.Node.NonElementParentNode](docs/DOM/Node/NonElementParentNode.md)
- [DOM.Node.ParentNode](docs/DOM/Node/ParentNode.md)
- [DOM.Node.Types](docs/DOM/Node/Types.md)
- [DOM.XHR.Types](docs/DOM/XHR/Types.md)
