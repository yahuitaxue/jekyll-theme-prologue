---
title: Mysqli
author: yahui
layout: post
---

Mysqli 事务处理

$obj = new mysqli('host','username','passwork','dbname','port');

if($obj->errno){

    die('Connect Error'.$obj->error);

}

$obj->set_charset('UTF8');

$obj->autocommit(FALSE);

$sql1 = '';

$result1 = $obj->query($sql1);

$res1 = $obj->affected_rows;

$sql2 = '';

$result2 = $obj->query($sql2);

$res2 = $obj->affected->rows;

if($result1 && $res1 >0 && $result2 && $res2 >0){

    $obj->commit();

    $obj->autocommit(TRUE);

}else{

    $obj->rollback();

}

////////////////////////////////////////////////////////////////////////////

Mysqli 多查询

$result = $obj->multi_query('select * from users; select * from goods;');

$aa = $obj->store_result();

var_dump($aa->fetch_all(MYSQLI_ASSOC));

$obj->next_result();

$aa = $obj->store_result();

var_dump($aa->fetch_all(MYSQLI_ASSOC));