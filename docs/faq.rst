Frequently Asked Questions
============

How do I add filter transmission curves?
--------
Each transmission curve should be in its own file named ``filter_name.par``,
where ``filter_name`` is a unique identifier that will be used to identify the filter in the code
(e.g., ``galex_FUV.par``).

Then, make ``<filter_name>.par`` a two-column space delimited ascii file where
the first column is wavelength in Angstroms and
the second column is detector signal per photon (arbitrarily normalized).
Comments *must* be preceded by a ``#``.
Then you can access it in python easily with e.g.

.. code-block:: python

		from sedpy import observate
		filt = observate.Filter("filter_name", directory="/path/to/the/file/")
		filt_list = observate.load_filters(["filter_name"], directory="/path/to/the/file/")

If using ``load_filters`` then all transmission files must be in the same directory.
Optionally you can place the files you create  in the ``<download_dir>/sedpy/sedpy/data/filters/`` directory
and reinstall with ``cd <download_dir>/sedpy; pip install .``.
Then you don't need to specify the ``directory`` keyword.

The new filter will now be accesible using ``filter_name``

.. code-block:: python

		from sedpy import observate
		filt = observate.Filter("filter_name")

Finally, you can simply pass a tuple of ``(wavelength, transmission)``:

.. code-block:: python

		from sedpy import observate
		filt = observate.Filter("filter_name", data=(wavelength, transmission)
