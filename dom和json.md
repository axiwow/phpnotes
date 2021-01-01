$dom = new DOMDocument('1.0','utf-8');

$book = $dom->appendChild($dom->createElement('book'));

$dom->createTextNode('文本节点');

$book->setAttribute('age',22);

$dom->formatOutput=true;

echo $dom->saveXML();

$str<<<xml

<?xml version="1.0" encoding="utf-8"?>

<html></html>

xml;

$book = simplexml_load_string($str);

$book->addChild('ewe','ewwe');

$book->addAttribute(‘sx','value');

$book->asXML();

$dom=new DOMDocument();

$char = $dom->getElementsByTagName('char')

foreach($char as $key=>$value){

    $value->item(0)->firstChild->nodeValue;

}
$dom->getElementsByTagName('char')[0]->item(0)->attributes;getAttribute('shuxingming');


$book = simplexml_load_string($string);

$book->node->node1[0]->name[0]['属性名'];

json_encode将数组转化为json

json_decode将json转化为数组，第二个参数为true返回数组，为false返回对象


