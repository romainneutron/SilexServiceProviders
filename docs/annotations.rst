Using annotations for Doctrine metadata
=======================================

Doctrine can read Enitiy/Document mapping metadata from docBlocks. You'll need then some extra configuration:

Put this somewhere in your bootstrap file, **after** having loaded your ``Doctrine*ServiceProvider``.
The order is important because of the automatic registration of doctrine classes autoloading.

If you have manually registered the autoloading of Doctrine files, you can put this whereveryou want **after** the autoload registration.


Registering
-----------

.. code-block:: php

    use Doctrine\Common\Annotations\AnnotationRegistry;

    AnnotationRegistry::registerLoader(function($class) use ($loader) {
    $loader->loadClass($class);
        return class_exists($class, false);
    });
    AnnotationRegistry::registerFile(__DIR__.'/vendor/doctrine_orm/lib/Doctrine/ORM/Mapping/Driver/DoctrineAnnotations.php');

