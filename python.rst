Python module
=============

Parts of Horzion EDA are available as a python module for use in scripts.

Installation
~~~~~~~~~~~~

The python module isn't included in the :code:`all` target.  To build it, run :code:`make horizon.so`. This requires the python 3 headers to be installed. You can then place it in python's :code:`sys.path` and import it using :code:`import horizon`.

Usage
~~~~~

::

	import horizon

	#open project
	p=horizon.Project("/path/to/project.hprj")

	#open schematic
	sch = p.open_top_schematic()

	#export PDF
	pdf_settings = sch.get_pdf_export_settings()
	pdf_settings['output_filename'] = '/tmp/sch.pdf'
	sch.export_pdf(pdf_settings)

	#export BOM
	bom_settings = sch.get_bom_export_settings()
	bom_settings['output_filename'] = '/tmp/bom.csv'
	sch.export_bom(bom_settings)

	#open board
	brd = p.open_board()

	#export gerber
	gerber_settings = brd.get_gerber_export_settings()
	gerber_settings["output_directory"] = "/tmp/gerber"
	brd.export_gerber(gerber_settings)

To further adjust the export settings, have a look at the dicts returned by the :code:`get_*_export_settings` methods.
