---
title: Java笔记1
date: 2006-10-05 21:18:02
tags: [Java]
categories: 
---
Instead of 
  
  String[] parameters = ( String [ ] )out.toArray ( ); 
  
 
  
 you could try: 
  
  
 Object[] o = out.toArray(); 
 String[] parameters=new String[o.length]; 
 System.arraycopy(o,0,parameters,0,parameters.length); 

more :

  String[] parameters = ( String [ ] )out.toArray ( new String[]{}); 

