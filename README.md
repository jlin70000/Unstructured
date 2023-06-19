Installation with ``conda`` on Windows
--------------------------------------

You can install and run ``unstructured`` on Windows with ``conda``, but the process
involves a few extra steps. This section will help you get up and running.

* Install `Anaconda <https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html>`_ on your Windows machine.
* Install Microsoft C++ Build Tools using the instructions in `this Stackoverflow post <https://stackoverflow.com/questions/64261546/how-to-solve-error-microsoft-visual-c-14-0-or-greater-is-required-when-inst>`_. C++ build tools are required for the ``pycocotools`` dependency.
* Run ``conda env create -f environment.yml`` using the ``environment.yml`` file in the ``unstructured`` repo to create a virtual environment. The environment will be named ``unstructured``.
* Run ``conda activate unstructured`` to activate the virtualenvironment.
* Run ``pip install unstructured`` to install the ``unstructured`` library.

===============================================
Setting up ``unstructured`` for local inference
===============================================

If you need to run model inferences locally, there are a few additional steps you need to
take. The main challenge is installing ``detectron2`` for PDF layout parsing. ``detectron2``
does not officially support Windows, but it is possible to get it to install on Windows.
The installation instructions are based on the instructions LayoutParser provides
`here <https://layout-parser.github.io/tutorials/installation#for-windows-users>`_.


# Unstructured
Document Parsing
Installation Steps
Run ``pip install pycocotools-windows``
Run ``git clone https://github.com/ivanpp/detectron2.git``, then ``cd detectron2``, then ``pip install -e .``
First, run ``git clone https://github.com/facebookresearch/iopath --single-branch --branch v0.1.8``. 
Then on line 753 in ``iopath/iopath/common/file_io.py`` change ``filename = path.split("/")[-1]`` to ``filename = parsed_url.path.split("/")[-1]``. 
After that, navigate to the ``iopath`` directory and run ``pip install -e .``.
* Run ``pip install unstructured[local-inference]``.
* 
====================
Installing PaddleOCR
====================
 Run ``conda install -c esri paddleocr``
 change the name of ``detectron2/tools`` to ``detectron2/detectron2_tools``
 Set the environment variable ``KMP_DUPLICATE_LIB_OK`` to ``"TRUE"``
 
==============
Error Output:
==============
 
 (unstructured) C:\Users\Jeremy Luo\source\repos\unstructured>python jpgparse.py
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:121: DeprecationWarning: pkg_resources is deprecated as an API
  warnings.warn("pkg_resources is deprecated as an API", DeprecationWarning)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:2870: DeprecationWarning: Deprecated call to `pkg_resources.declare_namespace('google')`.
Implementing implicit namespace packages (as specified in PEP 420) is preferred to `pkg_resources.declare_namespace`. See https://setuptools.pypa.io/en/latest/references/keywords.html#keyword-namespace-packages
  declare_namespace(pkg)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:2870: DeprecationWarning: Deprecated call to `pkg_resources.declare_namespace('mpl_toolkits')`.
Implementing implicit namespace packages (as specified in PEP 420) is preferred to `pkg_resources.declare_namespace`. See https://setuptools.pypa.io/en/latest/references/keywords.html#keyword-namespace-packages
  declare_namespace(pkg)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\util\dtype.py:26: DeprecationWarning: `np.bool8` is a deprecated alias for `np.bool_`.  (Deprecated NumPy 1.24)
  np.bool8: (False, True),
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\morphology\_skeletonize.py:241: FutureWarning: In the future `np.bool` will be defined as the corresponding NumPy scalar.
  0, 1, 1, 0, 0, 1, 0, 0, 0], dtype=np.bool)
Traceback (most recent call last):
  File "jpgparse.py", line 3, in <module>
    from paddleocr import PaddleOCR
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\__init__.py", line 14, in <module>
    from .paddleocr import *
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\paddleocr.py", line 37, in <module>
    from tools.infer import predict_system
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\tools\infer\predict_system.py", line 32, in <module>
    import tools.infer.predict_rec as predict_rec
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\tools\infer\predict_rec.py", line 31, in <module>
    from ppocr.postprocess import build_post_process
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\ppocr\postprocess\__init__.py", line 33, in <module>
    from .pg_postprocess import PGPostProcess
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\ppocr\postprocess\pg_postprocess.py", line 25, in <module>
    from ppocr.utils.e2e_utils.pgnet_pp_utils import PGNet_PostProcess
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\ppocr\utils\e2e_utils\pgnet_pp_utils.py", line 25, in <module>
    from extract_textpoint_slow import *
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\paddleocr\ppocr\utils\e2e_utils\extract_textpoint_slow.py", line 24, in <module>
    from skimage.morphology._skeletonize import thin
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\morphology\__init__.py", line 8, in <module>
    from ._skeletonize import skeletonize, medial_axis, thin, skeletonize_3d
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\morphology\_skeletonize.py", line 241, in <module>
    0, 1, 1, 0, 0, 1, 0, 0, 0], dtype=np.bool)
  File "C:\Projects\anaconda3\envs\unstructured\lib\site-packages\numpy\__init__.py", line 305, in __getattr__
    raise AttributeError(__former_attrs__[attr])
AttributeError: module 'numpy' has no attribute 'bool'.
`np.bool` was a deprecated alias for the builtin `bool`. To avoid this error in existing code, use `bool` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.bool_` here.
The aliases was originally deprecated in NumPy 1.20; for more details and guidance see the original release note at:
    https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations

================
Solution Attempt:
================
 
 conda create -n conda-env python=3.8 -y
conda activate conda-env
(conda-env) python -m pip install -e .
 
 python -m pip uninstall numpy
 python -m pip install numpy==1.23.5
 ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
layoutparser 0.3.4 requires iopath, which is not installed.
fvcore 0.1.5.post20221221 requires iopath>=0.1.7, which is not installed.
 
 python -m pip install iopath==0.1.7
 python -m pip install layoutparser==0.3.4 fvcore==0.1.5.post20221221

================
Error Message:
================
 C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:121: DeprecationWarning: pkg_resources is deprecated as an API
  warnings.warn("pkg_resources is deprecated as an API", DeprecationWarning)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:2870: DeprecationWarning: Deprecated call to `pkg_resources.declare_namespace('google')`.
Implementing implicit namespace packages (as specified in PEP 420) is preferred to `pkg_resources.declare_namespace`. See https://setuptools.pypa.io/en/latest/references/keywords.html#keyword-namespace-packages
  declare_namespace(pkg)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\pkg_resources\__init__.py:2870: DeprecationWarning: Deprecated call to `pkg_resources.declare_namespace('mpl_toolkits')`.
Implementing implicit namespace packages (as specified in PEP 420) is preferred to `pkg_resources.declare_namespace`. See https://setuptools.pypa.io/en/latest/references/keywords.html#keyword-namespace-packages
  declare_namespace(pkg)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\morphology\_skeletonize.py:241: DeprecationWarning: `np.bool` is a deprecated alias for the builtin `bool`. To silence this warning, use `bool` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.bool_` here.
Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
  0, 1, 1, 0, 0, 1, 0, 0, 0], dtype=np.bool)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\morphology\_skeletonize.py:256: DeprecationWarning: `np.bool` is a deprecated alias for the builtin `bool`. To silence this warning, use `bool` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.bool_` here.
Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
  0, 0, 0, 0, 0, 0, 0, 0, 0], dtype=np.bool)
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\restoration\inpaint.py:6: DeprecationWarning: Please use `laplace` from the `scipy.ndimage` namespace, the `scipy.ndimage.filters` namespace is deprecated.
  from scipy.ndimage.filters import laplace
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\feature\_orb_descriptor_positions.py:8: DeprecationWarning: loadtxt(): Parsing an integer via a float is deprecated.  To avoid this warning, you can:
    * make sure the original data is stored as integers.
    * use the `converters=` keyword argument.  If you only use
      NumPy 1.23 or later, `converters=float` will normally work.
    * Use `np.loadtxt(...).astype(np.int64)` parsing the file as
      floating point and then convert it.  (On all NumPy versions.)
  (Deprecated NumPy 1.23)
  POS = np.loadtxt(os.path.join(this_dir, "orb_descriptor_positions.txt"),
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\filters\_unsharp_mask.py:2: DeprecationWarning: Please use `gaussian_filter` from the `scipy.ndimage` namespace, the `scipy.ndimage.filters` namespace is deprecated.
  from scipy.ndimage.filters import gaussian_filter
C:\Projects\anaconda3\envs\unstructured\lib\site-packages\skimage\segmentation\random_walker_segmentation.py:49: DeprecationWarning: distutils Version classes are deprecated. Use packaging.version instead.
  if Version(scipy.__version__) >= Version('1.1'):
[2023/06/14 10:04:35] ppocr WARNING: Since the angle classifier is not initialized, the angle classifier will not be uesd during the forward process
 
==========================
New Python Script Changes:
==========================

 from langchain.document_loaders import UnstructuredFileLoader
from langchain.document_loaders import UnstructuredURLLoader

loader = UnstructuredFileLoader("jpgparsepicture2.jpg")

docs = loader.load()
print(docs[0].page_content[:200])
 
 unzip Poppler https://blog.alivate.com.au/poppler-windows/  (extract files and make sure it is under "unstructured")
 tesseract https://github.com/UB-Mannheim/tesseract/wiki
 add POPPLER BIN and Tesseract to PATH using the correct path
 
 pip install tesseract
 pip install pytesseract
 pip install langchain
 pip list (make sure langchain is there)

 If an error like this occurs: " Attempting uninstall: PyYAML
    Found existing installation: PyYAML 5.3.1
ERROR: Cannot uninstall 'PyYAML'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.\"
 Then:
 Force Reinstallation: You can try to force the reinstallation of the PyYAML package, which might resolve any conflicts. In your terminal or command prompt, use the following command:
 "pip install --ignore-installed PyYAML"
 This command will reinstall PyYAML and ignore the existing installation.
 
 Try again, "python < enter python script file >"
 
 =============
 .py to .exe:
 =============
(unstructured) C:\Users\Jeremy Luo\source\repos\unstructured>worddocparse.exe
Traceback (most recent call last):
  File "worddocparse.py", line 1, in <module>
    from unstructured.partition.auto import partition
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 385, in exec_module
  File "unstructured\partition\auto.py", line 15, in <module>
    from unstructured.partition.doc import partition_doc
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 385, in exec_module
  File "unstructured\partition\doc.py", line 8, in <module>
    from unstructured.partition.docx import partition_docx
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 385, in exec_module
  File "unstructured\partition\docx.py", line 29, in <module>
    from unstructured.partition.text_type import (
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 385, in exec_module
  File "unstructured\partition\text_type.py", line 14, in <module>
    from unstructured.nlp.english_words import ENGLISH_WORDS
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 385, in exec_module
  File "unstructured\nlp\english_words.py", line 12, in <module>
    with open(ENGLISH_WORDS_FILE) as f:
FileNotFoundError: [Errno 2] No such file or directory: 'C:\\Users\\Jeremy Luo\\AppData\\Local\\Temp\\_MEI196722\\unstructured\\nlp\\english-words.txt'
[10120] Failed to execute script 'worddocparse' due to unhandled exception!
 

