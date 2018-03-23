---
id: 112
disqus_id: 112 http://regis.decamps.info/blog/?p=112
title: Classe PHP pour Oracle
date: 2005-09-21T20:13:36+00:00
excerpt: 'Cette classe PHP permet de faire des requêtes Oracle avec une syntaxe proche des fonctions mysql_*'
layout: post
guid: http://regis.decamps.free.fr/wordpress/?p=112
permalink: /blog/2005/09/classe-php-pour-oracle/

dsq_thread_id:
  - "641606534"
categories:
  - Dev
tags:
  - PHP
---
Objectif
======
  
J’ai écrit cette classe lorsque j’avais besoin d’utiliser une base de données Oracle dans un petit projet PHP à l'\[Université de Manchester\] (http://cs.man.ac.uk/). L’objectif était triple:
  
* éviter d’avoir a entrer des variables paramètres de configuration à chaque accès à la base Oracle (factorisation du code)
  
* offrir une interface proche de celle de mysql, que je connaissais mieux (merci à l’abstraction)
  
* offrir des fonctionnalités plus poussées que celles offertes par les fonctions natives <tt>ora_*</tt>

Je ne sais pas si cette classe est encore d’actualité (je ne fais plus de PHP) mais elle pourra sans doute servir à d’autres.
  
Code
  
====

```
<?
 /**
  * PHP Class to ease the access of the Oracle Database in the University
  * of Manchester.
  * It mimics the mysql_* functions.
  *
  * Copyright (C) 2003 - Regis Decamps <decamps@users.sf.net>
  *
  *
  * This library is free software; you can redistribute it and/or
  * modify it under the terms of the GNU Lesser General Public
  * License as published by the Free Software Foundation; either
  * version 2.1 of the License, or (at your option) any later version.
  *
  * This library is distributed in the hope that it will be useful,
  * but WITHOUT ANY WARRANTY; without even the implied warranty of
  * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
  * Lesser General Public License for more details.
  *
  * You should have received a copy of the GNU Lesser General Public
  * License along with this library; if not, write to the Free Software
  * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307
  * USA
  * /
  
 class DataBase {
  
 /* connection index. */
 var $conn;   // the connection handler
 var $cursor; // internal Oracle cursor
 var $dbuser; //user to connect to the database
 var $dbpass; //password to connect to the database
  
  
 /** [public] Constructor.
  * Constructs a ressource to query the Oracle database.
  *@argument user The user name to connect the database to.
  *@argument password The password associated to this username
  */
 function DataBase($user=DBUSER,$password=DBPASS) {
 $this->dbuser=$user;
 $this->dbpass=$password;
  
 // Set environment variables
 putenv("TWO_TASK=teach.cs.man.ac.uk");
 putenv("TNS_ADMIN=/home/oracle/app/oracle/product/8.1.6/network/config/tcp_cs_man_ac_uk");
 putenv("ORACLE_HOME=/home/oracle/app/oracle/product/8.1.6");
 register_shutdown_function(array($this, '_database'));
 }
  
 /** [private]
  * Effectively connect to the database.
  */
 function connect() {
 if (!$this->conn) {
 $this->conn= ora_logon($this->dbuser,$this->dbpass);
 }
 }
  
 /** [private]
  * Nicely close the connection to the database.
  * You may want to call the function when you don't need the database
  * object any more.
  */
 function close() {
 if ($this->conn) {
 @ora_close($this->cursor);
 $ret=ora_logoff($this->conn);
 if (!$ret) {
 user_error('Cannot disconnect from '.$this->conn);
 }
 }
 }
  
 /** [private] Destructor.
  * This is the destructor (automatically called by PHP when the script
  * finishes). It makes a call to close()
  *@see #close
  */
 function _database() {
 //user_error ( 'Destructor of database object called.',E_USER_NOTICE );
 $this->close();
 }
  
  
 /*
  * db_query() sends a query to the currently active database on the
  * server.
  * Prints an error message in case of problem.
  *@return TRUE if success
  *@return FALSE if not
  */
 function query($query_string) {
 /* Connect if not done yet */
 $this->connect();
  
 if(!$this->conn) {
 user_error('User '.$this->dbuser.' failed to connect to 
 database.',E_USER_WARNING);
 }
 $this->cursor=@ora_do($this->conn,$query_string);
 if(!$this->cursor) {
 //user_error('Syntax error in query '.$query_string.': ['.ora_errorcode().'] '.ora_error(),E_USER_WARNING);
 return FALSE;
 }
 return TRUE;
 }
  
 /**
 * Returns an array that corresponds to the fetched row, or FALSE  if
 * there are no more rows.
 *@return the next row, if any
 *@return NULL otherwise
 *@see mysql_fetcharray
 */
 function fetch_array() {
 $retval=array();
 if(!$this->cursor) {
 return NULL;
 }
 $nbcols=@ora_numcols($this->cursor);
 for($i=0; $i&lt;$nbcols; $i++){    // parse throught cols
       $retval[$i]=ora_getcolumn($this->cursor,$i);
        $retval[ora_columnname($this->cursor,$i)]=ora_getcolumn($this->cursor,$i);
     }
 if (!ora_fetch($this->cursor)) {
 ora_close($this->cursor);
 $this->cursor=0;
 }
 return $retval;
 }
  
 /** [public]
 * Returns the number of columns of the query
 * @return int: number of columns
 */
  
 function ncols(){
 $retval=@ora_numcols($this->cursor);
 return $retval;
 }
  
 } //end class DataBase
 ?>
```
