<?php include_once("conn.php"); ?>
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Untitled Document</title>
</head>

<body>
<h2>Unidades por produtos
</h2>
<table width="500" border="1" cellpadding="5">
  <tr>
    <th scope="col">PRODUTO</th>
    <th scope="col">UNIDADES VENDIDAS</th>
  </tr>
  
  	<?php 
	
	$sql1="select p.PRODUTO, count(v.ID_PRODUTO) as 'UNIDADES' from tb_produtos p inner join tb_vendas v on p.ID_PRODUTO=v.ID_PRODUTO group by p.PRODUTO;";
	
	$exec=mysqli_query($conn,$sql1) or die("FALHA DE EXECUÇÃO sql.");
	
	while($dados=mysqli_fetch_array($exec)){
	
	
	?>
  
  <tr>
    <td><?php echo $dados['PRODUTO'];?></td>
    <td><?php echo $dados['UNIDADES'];?></td>
  </tr>
  
  		<?php 
		
	}
		?>		
  
</table>
</body>
</html>
