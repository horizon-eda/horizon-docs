Python module
=============

Parts of Horzion EDA are available as a python module for use in scripts.

Installation
~~~~~~~~~~~~

The python module isn't included in the :code:`all` target.  To build it, run :code:`make build/horizon.so`. This requires the python 3 headers to be installed. You can then place it in python's :code:`sys.path` and import it using :code:`import horizon`.

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

	#export pick&place
	pnp_settings = brd.get_pnp_export_settings()
	pnp_settings["output_directory"] = "/tmp/pnp"
	brd.export_pnp(pnp_settings)

	#export STEP
	step_settings = brd.get_step_export_settings()
	step_settings["filename"] = "/tmp/pca.step"
	brd.export_step(step_settings)

	#run DRC
	rules=brd.get_rules()
	#modify rules if needed
	rule_ids = brd.get_rule_ids()
	#if needed, remove unneeded checks from rule_ids
	result = brd.run_checks(rules, ids)

To further adjust the export settings, have a look at the dicts returned by the :code:`get_*_export_settings` methods.
