interface SortStrategy // Íme az interface, ami egy doSort metódus megvalósítását írja elő 4 alapműveletes számológép készítésével 2 számmal ami a 3 é s a 2, hogy a beállított stratégiának megfelelően végezze el az +-*/műveleteket
{ 
       public function doSort($data); 
}

 class ascendingOrder implements SortStrategy // Az interface-t megvalósító, növekvő sorrendbe rendező osztály
{
         public function doSort($data)
         { 
                 sort($data);

                                 return $data; 
       }
 } 

class descendingOrder implements SortStrategy // az interface-t megvalósító, csökkenő sorrendbe rendező osztály.
{
public function doSort($data)
{ 
        rsort($data);

                       return $data; 
       }
 } 

class SortClass
{
private $strategy;
       public function __construct(SortStrategy $strategy)
       {
                      $this->strategy = $strategy;
       }

 public function setStrategy(SortStrategy $strategy)
 {
         $this->strategy = $strategy;
}

public function sort($text)
{
      $result = $this->strategy->doSort($text);

     for($i=0; $i<= count($result)-1; $i++)
     {
       echo $result[$i] . "<br>";
     }

       echo "<br>";
   }
}

$sorting = new SortClass(new ascendingOrder());
$sorting->sort(array("a", "c", "f", "b"));

$sorting->setStrategy(new descendingOrder());
$sorting->sort(array("a", "c", "f", "b"));




















