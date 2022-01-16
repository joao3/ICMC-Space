# ICMC-Space

Apresentação: https://drive.google.com/file/d/1N1ToV9FCuG99xgIo0zicKiDAorXpCfhe/view?usp=sharing

Apresentação Individual Eduardo
https://drive.google.com/file/d/1xPrV2QdHg7FKZT_D9-Gy7actlpmA5DvJ/view?usp=sharing

## Rotina de impressão dos pontos

```
loadn r1, #582  		; Posição para imprimir os pontos
	load r0, score 			; r0 = score
	loadn r2, #100 			; r2 = 100
	div r3, r0, r2 			; r3 = r0 / r2    ->   pega o dígito da centena
	loadn r4, #48 			; r4 = 48
	add r3, r3, r4 			; r3 += r4  ->  converte o dígito para o seu valor na tabela ASCII, por exemplo o dígito 5 é representado pelo número 53 na tabela
	outchar r3, r1 			; imprime a centena
	sub r3, r3, r4 			; r3 -= r2  ->  volta do valor da tabela ASCII para o dígito
	mul r3, r3, r2 			; r3 *= r2  ->  multiplica o dígita da centena por 100
	sub r0, r0, r3 			; r0 -= r3  ->  remove as centenas

							; EXEMPLO:
							; 523 -> 523 / 100 = 5 -> dígito da centena = 5 -> imprime o 5 -> subtrai 5 * 100 do total de pontos ->
							; -> 523 - 5 * 100 = 23 -> segue processo análogo para dezena e unidade

	; Impressão da dezena
	inc r1
	loadn r2, #10 
	div r3, r0, r2 
	loadn r4, #48
	add r3, r3, r4
	outchar r3, r1
	sub r3, r3, r4
	mul r3, r3, r2
	sub r0, r0, r3

	; Impressão da unidade
	inc r1
	add r0, r0, r4
	outchar r0, r1
```
## Como jogar
### Movimentos
As teclas A e D são as responsáveis por movimentar a nave para a esquerda e direita respectivamente.

### Disparo
O espaço é o responsável por efetuar o disparo

## Telas

### Inicial
![Tela inicial](https://user-images.githubusercontent.com/54045014/149681001-5d547905-6a5b-49d1-84ec-bb9c3b108a38.png)

### Jogo
![Jogo](https://user-images.githubusercontent.com/54045014/149681042-591dba73-2333-4530-8e3e-17e8fad1f198.gif)

### Game Over
![image](https://user-images.githubusercontent.com/54045014/149681169-73f995be-def1-4f96-bfdd-a718c9606a2f.png)



