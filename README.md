[![Build Status](https://travis-ci.org/Funz/plugin-Python.png)](https://travis-ci.org/Funz/plugin-Python)

# Funz plugin: Python 3

This plugin is dedicated to launch Python 3 calculations from Funz.
It supports the following syntax and features:

* Input
  * file type supported: '*.py', any other format for resources
  * parameter syntax: 
    * variable syntax: `?[...]`
    * formula syntax: `${...}`
    * comment char: `#`
  * example input file:
  ```
  import math as m
  def branin(x1,x2):
      x1 = x1*15-5
      x2 = x2*15

      return (x2 - 5/(4*m.pi^2)*(x1^2) + 5/m.pi*x1 -6 )^2 + 10*(1-1/(8*m.pi))*m.cos(x1) +10
  print( "z={0}".format( branin( ?[x1~[1,2]], ${x2 +1.23} | #.###)))
  ```
     * will identify input:
       * x1, expected to vary inside [1,2]
       * x2, expected to vary inside [0,1] (by default)
     * replace `!{?x2 + 1.23 | #.###}` expression by its evaluation

* Output
  * file type supported: 'out.txt'
  * read any named value printed with `=`, like `print("z={0}".format(1.234))`
  * example output file:
  ```
  import math as m
  def branin(x1,x2):
      x1 = x1*15-5
      x2 = x2*15

      return (x2 - 5/(4*m.pi**2)*(x1**2) + 5/m.pi*x1 -6 )**2 + 10*(1-1/(8*m.pi))*m.cos(x1) +10

  print( "z={0}".format( branin( 0.5, 0.132) ) )
  ```
  * will return output:
    * z=3.000715


![Analytics](https://ga-beacon.appspot.com/UA-109580-20/plugin-Python)
