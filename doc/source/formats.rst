.. _formats:

.. index:: formats

File Formats
============

Emperor uses two main files as inputs, a mapping file and a coordinates file,
here we will describe their structure.

Mapping File
^^^^^^^^^^^^

A mapping file refers to the additional information collected about your
samples, some common examples are body site, collection time, pH, latitude,
longitude, etc. This information is used by Emperor to color and modify visual
aspects of your plot in a systematic way.

Mapping files should conform to the format as described by `QIIME
<http://qiime.org/documentation/file_formats.html#metadata-mapping-files>`_.
**Note** that the only required column is `SampleID`, if this column is not
present the file will not be parsed correctly and the script will bring up an
error.

Coordinates File
^^^^^^^^^^^^^^^^

Coordinates files describe the position in which each of the samples should be
placed in space, as of version `0.9.4-dev` there are two different file
formats that are accepted by Emperor:

**Classic Format**

This format is tab-delimited and must include the following information (
versions of QIIME <= 1.8.0 generate this file when you execute
`principal_coordinates.py`):

- The first line is the header for each of the dimensions.
- For each of the samples in your dataset you'll find a line with a sample
  identifier and its value at each dimension. If you have 7 samples you should
  expect to see 7 lines with coordinates spanning through 7 dimensions.
- Two empty lines.
- A line with an eigenvalue for each dimension.
- A line with the percentages of variation explained at each dimension.

See the example below that presents a dataset where 5 samples were included.

.. code-block:: none

    pc vector number	1	2	3	4	5
    PC.636	0.333514620475	0.081687	0.25081	0.103746	2.50106743521e-09
    PC.635	0.258145479886	-0.22437	-0.25446	-0.0290044	2.50106743521e-09
    PC.356	-0.270663791669	-0.23983	0.18965	-0.118931	2.50106743521e-09
    PC.481	-0.0437436047686	0.30751	-0.077078	-0.20627	2.50106743521e-09
    PC.354	-0.277252703922	0.074945	-0.10898	0.245681	2.50106743521e-09


    eigvals	0.329912543767	0.2147172	0.1815366	0.1261003	-3.127915774e-17
    % variation explained	38.68853	25.18276	21.2717	14.85772	3.667478e-15

**scikit-bio Ordination Results**

Emperor is also capable of parsing files generated by scikit-bio's
`OrdinationResults <http://scikit-bio.org/docs/latest/generated/skbio.io.ordination.html>`_
class.
