# Clave-de-acceso-SRI
Calculo del dígito verificar de la estructura de la clave de acceso.
<?php
class modulo{
	function getMod11Dv( $num ){
	
	  $digits = str_replace( array( '.', ',' ), array( ''.'' ), strrev($num ) );
	  if ( ! ctype_digit( $digits ) )
	  {
	    return false;
	  }

	  $sum = 0;
	  $factor = 2;
	 
	  for( $i=0;$i<strlen( $digits ); $i++ )
	  {
	    $sum += substr( $digits,$i,1 ) * $factor;
	    if ( $factor == 7 )
	    {
	      $factor = 2;
	    }else{
	     $factor++;
	   }
	  }
	 
	  $dv = 11 - ($sum % 11);
	  if ( $dv == 10 )
	  {
	    return 1;
	  }
	  if ( $dv == 11 )
	  {
	    return 0;
	  }
	  return $dv;
	}
}
$dig = new modulo();
echo $dig->getMod11Dv('050320200717231252640012001002000001193050320001');
?>

