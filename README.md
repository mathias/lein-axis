# lein-axis
Simple Leiningen plug-in to speed up working with Apache Axis and WSDL files

## Usage
Use Apache Axis to generate Java classes for WSDL files.

You will need to add Apache Axis to your project as a dependency, e.g.:
    :dependencies [[org.clojure/clojure "1.5.1"]
                   [axis/axis "1.4"]]

Also, this plug-in should be added to your project as a plugin:

    :plugins [[lein-axis "0.2"]]

Then, to configure what WSDL files to use and where to put the generated
source files:

    :java-source-path "src/java"
    :axis [["src/wsdl/myservice.wsdl" "generated.myservice"]
           ["src/wsdl/myotherservice.wsdl" "generated.myotherservice"]]

Then, simply run:

    $ lein deps
    $ lein axis

Note that :java-source-path is used by the lein-javac plug-in, which is
probably the easiest way to turn the Java code generated into compiled
classes. lein-axis uses this setting as the target directory (for the
root of the generated packages). src/java is used as a default if you
don't provide this value.

If you're generating server-side classes, or need to add extra arguments,
you can do this per-WSDL file, like so:

    :axis ["src/wsdl/myservice.wsdl" "generated.myservice" ["-s"]]


## License

Copyright (C) 2010 James Aley.

Distributed under the Eclipse Public License, the same as Clojure.
