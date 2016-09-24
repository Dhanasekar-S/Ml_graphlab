
# Fire up GraphLab Create


```python
import graphlab
```


```python
# load tabular data set

```


```python
sf=graphlab.SFrame('people-example.csv')
```

    [ERROR] graphlab.connect.main:  ========================================
    GraphLab Create requires a license to use. To get a trial, non-commercial,  or commercial license, visit https://turi.com/register.
    =================================================
    



    ---------------------------------------------------------------------------

    InvalidProductKey                         Traceback (most recent call last)

    <ipython-input-3-3043300fead2> in <module>()
    ----> 1 sf=graphlab.SFrame('people-example.csv')
    

    /opt/conda/lib/python2.7/site-packages/graphlab/data_structures/sframe.pyc in __init__(self, data, format, _proxy)
        865             self.__proxy__ = _proxy
        866         else:
    --> 867             self.__proxy__ = UnitySFrameProxy(glconnect.get_client())
        868             _format = None
        869             if (format == 'auto'):


    /opt/conda/lib/python2.7/site-packages/graphlab/connect/main.pyc in get_client()
        138     """
        139     if not is_connected():
    --> 140         launch()
        141     assert is_connected(), ENGINE_START_ERROR_MESSAGE
        142     return __CLIENT__


    /opt/conda/lib/python2.7/site-packages/graphlab/connect/main.pyc in launch(server_addr, server_bin, server_log, auth_token, server_public_key)
         90         if server:
         91             server.try_stop()
    ---> 92         raise e
         93     server.set_log_progress(True)
         94     # start the client


    InvalidProductKey: Product key not found.



```python
# Set product key on this computer. After running this cell, you will not need to re-enter your product key. 
graphlab.product_key.set_product_key('B119-B174-358D-D3A7-C18B-63DD-E1B8-9ED9')

# Limit number of worker processes. This preserves system memory, which prevents hosted notebooks from crashing.
graphlab.set_runtime_config('GRAPHLAB_DEFAULT_NUM_PYLAMBDA_WORKERS', 4)

# Output active product key.
graphlab.product_key.get_product_key()
```

    /opt/conda/lib/python2.7/site-packages/requests/packages/urllib3/connection.py:266: SubjectAltNameWarning: Certificate for beta.graphlab.com has no `subjectAltName`, falling back to check for a `commonName` for now. This feature is being removed by major browsers and deprecated by RFC 2818. (See https://github.com/shazow/urllib3/issues/497 for details.)
      SubjectAltNameWarning
    [INFO] graphlab.cython.cy_server: GraphLab Create v2.0.1 started. Logging: /tmp/graphlab_server_1471416930.log


    This non-commercial license of GraphLab Create for academic use is assigned to dharun199531@gmail.com and will expire on August 17, 2017.





    'B119-B174-358D-D3A7-C18B-63DD-E1B8-9ED9'




```python
sf=graphlab.SFrame('people-example.csv')
```


<pre>Finished parsing file /home/jovyan/work/Week 1/people-example.csv</pre>



<pre>Parsing completed. Parsed 7 lines in 0.016007 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[str,str,str,int]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------



<pre>Finished parsing file /home/jovyan/work/Week 1/people-example.csv</pre>



<pre>Parsing completed. Parsed 7 lines in 0.015201 secs.</pre>



```python
sf

```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>



# Graphlab Canvas


```python
sf.show()

```

    Canvas is accessible via web browser at the URL: http://localhost:46662/index.html
    Opening Canvas in default web browser.



```python
graphlab.canvas.set_target('ipynb')
```


```python
sf['age'].show(view='Categorical')
```




```python
sf['Full Name']=sf['First Name']+sf[Last Name]
```


      File "<ipython-input-10-644012c1f330>", line 1
        sf['Full Name']=sf['First Name']+sf[Last Name]
                                                    ^
    SyntaxError: invalid syntax




```python
sf['Full Name']=sf['First Name']+' '+sf['Lat Name']
```


    ---------------------------------------------------------------------------

    RuntimeError                              Traceback (most recent call last)

    <ipython-input-11-3121e0bd224e> in <module>()
    ----> 1 sf['Full Name']=sf['First Name']+' '+sf['Lat Name']
    

    /opt/conda/lib/python2.7/site-packages/graphlab/data_structures/sframe.pyc in __getitem__(self, key)
       3997             return self._row_selector(key)
       3998         elif type(key) is str:
    -> 3999             return self.select_column(key)
       4000         elif type(key) is type:
       4001             return self.select_columns([key])


    /opt/conda/lib/python2.7/site-packages/graphlab/data_structures/sframe.pyc in select_column(self, key)
       3600             raise TypeError("Invalid key type: must be str")
       3601         with cython_context():
    -> 3602             return SArray(data=[], _proxy=self.__proxy__.select_column(key))
       3603 
       3604     def select_columns(self, keylist):


    /opt/conda/lib/python2.7/site-packages/graphlab/cython/context.pyc in __exit__(self, exc_type, exc_value, traceback)
         47             if not self.show_cython_trace:
         48                 # To hide cython trace, we re-raise from here
    ---> 49                 raise exc_type(exc_value)
         50             else:
         51                 # To show the full trace, we do nothing and let exception propagate


    RuntimeError: Runtime Exception. Column name Lat Name does not exist.



```python
sf['Full Name']=sf['First Name']+' '+sf['Last Name']
```


```python
sf

```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>




```python

```
