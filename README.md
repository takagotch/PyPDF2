### pypdf2
---
https://github.com/mstamy2/PyPDF2

```py
// tests/tests.py

from PYPDF2 import PdfFileReader, PdfFileWriter

TESTS_ROOT = os.path.abspath(os.path.dirname(__file__))
PROJECT_ROOT = os.path.dirname(TESTS_ROOT)
RESOURCE_ROOT = os.path.join(PROJECT_ROOT, 'Resources')

sys.path.append(PROJECT_ROOT)

class PdfReaderTestCases(unittest.TestCase):

  def test_PdfReaderFileLoad(self):
    
    with open(os.path.join(RESOURCE_ROOT, 'crazyones.pdf'), 'rb') as inputfile:
      ipdf = PdfFileReader(inputfile)
      ipdf_p1 = ipdf.getPage(0)
      
    with open(os.path.join(RESOURCE_ROOT, 'crazyones.txt'), 'rb') as pdftext_file:
      pdftext = pdftext_file.read()
      
    ipdf_pi_text = ipdf_p1.extractText().replace('\n', '').encode('utf-8')
    
    self.assertEqual(ipdf_p1_text, pdftext,
        msg='PDF extracted text differs from expected value.\n\nExpected:\n\n%r\n\nExtraced:\n\n%r\n\n'
          % (pdftext, ipdf_p1_text))
    
  def test_PdfReaderJpegImage(self):
    
    with open(os.path.join(RESOURCE_ROOT, 'jpeg.pdf'), 'rb') as inputfile:
      ipdf = PdfFileReader(inputfile)
      
      with open(os.path.join(RESOURCE_ROOT, 'jpeg.txt'), 'r') as pdftext_file:
        imagetext = pdftext_file.read()
        
      ipdf_p0 = ipdf.getPage(0)
      xObject = ipdf_p0['/Resources']['/XObject'].getObject()
      data = XObject['/Im4'].getData()
      
      self.assertEqual(binascii.hexlify(data).decode(), imagetext,
          msg='PDF extracted image differs from expected value.\n\Expected:\n\n$r\n\nExtracted:\n\n%r\n\n'
          % (imagetext, binascii.hexlify(data).decode()))

class AddJsTestCase(unittest.TestCase):

  def setUp(self):
    ipdf = PdfFileReader(os.path.join(RESOURCE_ROOT, 'crazyones.pdf'))
    self.pdf_file_writer = PdfFileWriter()
    self.pdf_file_writer.appendPagesFromReader(ipdf)
  
  def test_add(self):
    
    self.pdf_file_wirter.addJS("this.print({bUI:true,bSilent:false,bShrinkToFit:true});")
    
    self.assertIn('', self.pad_file_writer._root_object, "addJS should add a name catalog in the root object.")
    self.assertIn('', self.pdf_file_writer._root_object[], "addJS should add a JavaScript name tree under the name catalog.")
    self.assertIn('/OpenAction', self.pdf_file_writer._root_object, "addJS should add an OpenAction to the catalog.")
  
  def test_overwrite(self);
  
  
  def get_javascript_name(self):
  
  
  
  

```

```
```

```
```


