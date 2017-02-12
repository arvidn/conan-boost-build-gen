Boost Build conan generator
---------------------------

This conan generator generates a ``project-root.jam`` file with ``lib`` targets
for all conan dependencies.

For example, a project depending on ``OpenSSL/1.0.2g@lasote/stable`` will have
the following targets generated::

	lib ssl :
		: # requirements
		<name>ssl
		<search>/Users/arvid/.conan/data/OpenSSL/1.0.2g/lasote/stable/package/811d822905b54fc167634e916129401c4f86d1e5/lib
		: # default-build
		: # usage-requirements
		<include>/Users/arvid/.conan/data/OpenSSL/1.0.2g/lasote/stable/package/811d822905b54fc167634e916129401c4f86d1e5/include
		;

	lib crypto :
		: # requirements
		<name>crypto
		<search>/Users/arvid/.conan/data/OpenSSL/1.0.2g/lasote/stable/package/811d822905b54fc167634e916129401c4f86d1e5/lib
		: # default-build
		: # usage-requirements
		<include>/Users/arvid/.conan/data/OpenSSL/1.0.2g/lasote/stable/package/811d822905b54fc167634e916129401c4f86d1e5/include
		;

In order to use this generator, add a dependency on it on your ``conanfile.txt``
and use the ``BoostBuild`` generator.

::

	[requires]
	BoostBuildGen/0.1@arvidn/testing

	[generators]
	BoostBuild

