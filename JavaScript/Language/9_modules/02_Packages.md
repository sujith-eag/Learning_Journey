
One of the advantages of building a program out of separate pieces, and being
able to run some of those pieces on their own, is that you might be able to
apply the same piece in different programs.


nd energy moving copies around and keeping them up-to-date.
That’s where packages come in. A package is a chunk of code that can be
distributed (copied and installed). It may contain one or more modules and
has information about which other packages it depends on. A package also
usually comes with documentation explaining what it does so that people who
didn’t write it might still be able to use it.
When a problem is found in a package or a new feature is added, the package
is updated. Now the programs that depend on it (which may also be packages)
can copy the new version to get the improvements that were made to the code.


___

Working in this way requires infrastructure. We need a place to store and find
packages and a convenient way to install and upgrade them. In the JavaScript
world, this infrastructure is provided by NPM (https://npmjs.org).
NPM is two things: an online service where you can download (and upload)
packages and a program (bundled with Node.js) that helps you install and
manage them.

ommand line program.
Having quality packages available for download is extremely valuable. It
means that we can often avoid reinventing a program that 100 people have
written before and get a solid, well-tested implementation at the press of a few
keys.


___
### CommonJS module

A CommonJS module looks like a regular script, but it has access to two
bindings that it uses to interact with other modules. The first is a function
called require. When you call this with the module name of your dependency,
it makes sure the module is loaded and returns its interface. The second is an
object named exports, which is the interface object for the module. It starts
out empty and you add properties to it to define exported values.

The transition of the JavaScript community from CommonJS style to ES
modules has been a slow and somewhat rough one. But fortunately we are now

at a point where most of the popular packages on NPM provide their code as ES
modules, and Node.js allows ES modules to import from CommonJS modules.
So while CommonJS code is still something you will run across, there is no real
reason to write new programs in this style anymore.

