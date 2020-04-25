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
	
	#export 3D rendering (see next section)
	exporter = brd.export_3d(1920, 1080) #width, height
	exporter.view_all()
	exporter.load_3d_models() #optional
	exporter.render_to_png("brd.png")

To further adjust the export settings, have a look at the dicts returned by the :code:`get_*_export_settings` methods.

3D rendering usage
~~~~~~~~~~~~~~~~~~

use :code:`brd.export_3d(1920, 1080)` or similar to get an Image3DExporter object

.. py:class:: Image3DExporter 

   .. py:method:: render_to_png(filename)

      Render to png image

   .. py:method:: render_to_surface()

      Render to pycairo surface

      :rtype: :py:class:`cairo.Surface`

   .. py:method:: load_3d_models()

      Loads 3D models if available

   .. py:method:: view_all()

      Resets view to top side

   .. py:attribute:: cam_azimuth
      :type: float

      Camera azimuth angle in degrees

   .. py:attribute:: cam_elevation
      :type: float

      Camera elevation angle in degrees

   .. py:attribute:: cam_fov
      :type: float

      Camera field of view in degrees

   .. py:attribute:: cam_distance
      :type: float

      Camera distance in millimeters

   .. py:attribute:: center_x
      :type: float

      Where the camera looks at (millimeter)

   .. py:attribute:: center_y
      :type: float

      Where the camera looks at (millimeter)

   .. py:attribute:: background_top_color
      :type: 3-tuple of float

      Background color at the top, components range from 0 to 1

   .. py:attribute:: background_bottom_color
      :type: 3-tuple of float

      Background color at the bottom, components range from 0 to 1

   .. py:attribute:: solder_mask_color
      :type: 3-tuple of float

      Solder mask color, components range from 0 to 1

   .. py:attribute:: substrate_mask_color
      :type: 3-tuple of float

      Color of the PCB body, components range from 0 to 1

   .. py:attribute:: ortho
      :type: bool

      Use orthographic projection

   .. py:attribute:: show_models
      :type: bool

      Show 3D models

   .. py:attribute:: show_silkscreen
      :type: bool

   .. py:attribute:: show_solder_mask
      :type: bool

   .. py:attribute:: show_solder_paste
      :type: bool

   .. py:attribute:: show_substrate
      :type: bool

   .. py:attribute:: use_layer_colors
      :type: bool

      Use layer colors from 2D view for copper layers
