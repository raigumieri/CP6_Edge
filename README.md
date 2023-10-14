<h1 align="center"> CheckPoint 6 - Projeto IOT </h1>

<h3> Integrantes do grupo: </h3>

<ul> 
  <li> RM550233 - Fellype Dos Santos Laes </li>
  <li> RM550539 - Guilherme Fazito </li>
  <li> RM551528 - Henrique Lima </li>
  <li> RM98860  - Ian Xavier Kuraoka </li>
  <li> RM98287  - Raí Gumieri dos Santos </li>
</ul>

<h2 align="center"> Introdução </h2>

<p align="justify"> Nessa nova etapa do projeto, vamos montar um pequeno protótipo que será usado para medir alguns parâmetros, envolvendo temperatura, umidade e luminosidade. Para isso, vamos precisar de alguns sensores de monitoramento, que seriam: </p>
<ul> 
 <li> ESP32; </li>
 <li> Placa de ensaio; </li>
 <li> DHT11 ou DHT22; </li>
 <li> Sensor LDR; </li>
 <li> Resistor 10kΩ. </li>
</ul>

<p align="justify"> Caso você não tenha os equipamentos em mãos, você pode acessar o site Wokwi e realizar o procedimento, assim vai conseguir acompanhar e entender como é feito na prática </p>
<h4> Link do site: https://wokwi.com/ </h4>

<p align="justify"> Para facilitar, vamos seguir o procedimento no próprio site Wokwi. A montagem dos componentes vai ficar dessa forma: </p>

<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/c94edba7-6598-4eda-9f5f-6c7b6351d346"> 
</div>

<br>


<div align="center"> 
<h2> Análise do Equipamento </h2>

<div align="justify"> 
  <p> O ESP32 vai ser muito importante nesse projeto, pois é graças a ele que vamos conseguir conectar a internet e salvar os valores obtidos pelos sensores na nuvem, sendo um processo bem eficiente quando você estiver longe do protótipo e deseja ter acesso as informações para saber sobre os dados coletados ou apenas analisar se o equipamento está funcionando normalmente. </p> 
  <p> Caso você consiga conectar o projeto a sua rede wifi, você pode acessar ele e poderá fazer alguns comandos, fazendo com que ele ligue e desligue o led do ESP32 ou pegar os dados dos sensores que estão sendo utilizados. Para isso, você pode baixar o aplicativo MyMQTT ou usar uma aplicação do Google Colab, para ter acesso as medições do aparelho. </p>
  <p> A placa de ensaio será de extrema importância, já que vai ser ela onde vamos fazer as devidas conexões entre o ESP32 e os sensores. </p>
  <p> Falando em sensores, o DHT22 serve para fazer a medição de temperatura e umidade, no projeto físico você pode usar o DHT11, ele consegue fazer a mesma medição, ou seja, independente do que você escolher, ambos vão gerar os mesmos resultados. </p>
  <p> Já o sensor LDR será utilizado para fazer a medição da luminosidade, divulgando como resposta a voltagem e o valor em porcentagem. </p>
</div>

<br>

<h2> Montagem do Código </h2>
<p align="justify"> Após ter concluído a montagem da imagem acima, vamos trabalhar no desenvolvimento do código. Você pode usar o que está sendo fornecido neste repositório, porém deve ser feito algumas alterações, envolvendo os tópicos que foram marcados no código. São eles que você terá que usar para acessar a nuvem e visualizar os dados que estão sendo fornecidos (Linhas 21, 22, 23, 24, 25 e 32).  </p>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/5bfc38cb-b5d8-4a14-a04a-d22c77c7000b">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/551e01f0-9944-4e45-827a-5e6090419949">
</div>

<br>

<div align="justify">
  <p> É necessário alterar o lamp108, pois ele é a porta onde você vai conseguir acessar a rede. Você pode alterar para lamp109, lamp110, etc...  </p>
  <p> No final dos 3 últimos tópicos, é possível analisar os finais “L, U, T”, essas são as siglas para identificar as portas em que estão os dados de Luminosidade, Umidade e Temperatura. </p>
  <p> Outra alteração importante é na parte do Wifi, é necessário que você coloque o nome e senha da sua internet, para que o ESP32 consiga se conectar à rede. Todavia, se estiver realizando o passo a passo pelo site, é necessário colocar “Wokwi-GUEST” no nome da     rede, sem colocar senha, pois o próprio site vai usar uma rede para conectar com o ESP32 (Linhas 41 e 42). </p>
</div>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/9c55c7b1-0c80-4b86-ba66-e658dd19bca2">
</div>

<br>

<p> Após essas modificações, pode ligar o código e esperar aparecer a informação de que o ESP32 está tentando se conectar a uma rede. </p>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/d7963852-47e0-4f12-bfc2-1343fac46a70">
</div>

<br>

<p> Caso você esteja fazendo com o material em mãos, é necessário apertar o botão de “BOOT” do ESP32 para fazer a conexão. </p>
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/ad286171-87de-4426-bc58-515b203c7fe7" height=200px>

<br>

<p> Após essa etapa aparecerá a seguinte informação: </p>
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/dda56039-c7bf-466b-b4e0-e1a283edbd84">
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/606f9783-6479-4d5e-91ce-ba5a83349e8d">

</div>
<br>

<p align="justify"> Agora vamos trabalhar com o Google Colab, primeiro é necessário instalar a biblioteca Paho MQTT, pois vamos usar ele para se comunicar com o broker (Porta 1883). </p>
<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/77ef62cf-9a0b-419f-a4b5-be549e529aa4">
</div>

<br>

<p align="center"> Após a instalação, vamos realizar a importação do Paho MQTT e acrescentar algumas linhas de código: </p>

<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/71851a71-2642-4ba0-86fd-4fbf22ec68f1">
</div>

<br>

<p align="justify"> Antes de você rodar o código, vale ressaltar que ele vai mostrar somente os valores de luminosidade, já que estamos utilizando a porta “/TEF/lamp108/attrs/l”. O resultado disso irá gerar: </p>

<table align="center"> 
  <tr>
    <td align="center"> Dados de Luminosidade </td>
    <td align="center"> Dados de Umidade </td>
    <td align="center"> Dados de Temperatura </td>
  </tr>
  <tr>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/b65a502e-f4dd-4aff-9066-5b9e0078f1a1"> </td>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/2a43ec2e-f519-40dd-9001-86f7df3c2157"> </td>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/f84d4bec-6da4-473e-9f4f-9a17e0fb8518"> </td>
  </tr> 
</table>

<br> 

<p align="justify"> Após esses passos, o projeto está finalizado. Agora é possível ter acesso aos dados de Temperatura, Umidade e Luminosidade em qualquer lugar de onde você estiver, desde que tenha acesso a internet para conseguir obter as informações.  </p>

