
Algoritmo "JogoDaVelha"

Procedimento PreencherMatriz()
Inicio
   para i <- 1 ate 3 faca
      para j de 1 ate 3 faca
         cont <- cont + 1
         jogo[i,j] <- NumpCarac(cont)

      fimpara
   fimpara

fimprocedimento
//--------------------------------------------------------------
procedimento velha ()
inicio

   escreval("===================")
   escreval("   JOGO DA VELHA   ")
   escreval("+-----+-----+-----+")

   para i <- 1 ate 3 passo 1 faca
      para j<-1 ate 3 passo 1 faca
         escreva("| ")
         escreva(jogo[i,j]:4)
      fimpara
      escreval("| ")
      escreval("+-----+-----+-----+")
   fimpara
   escreval("===================")

fimprocedimento

//--------------------------------------------------------------

procedimento jogar ()
inicio
   x<- "X"
   vencedor <- falso
   vez <- 0
   par <- 1

   repita

      escreval("Digite um numero para ", x,":")
      leia(op)

      se ( op > 0 ) e ( op < 10) entao
         //--------------------------------------------------------------
         se ( op > 0 ) e ( op < 4) entao
            L <- 1
            se (jogo[L,op] = "X") ou (jogo[L,op] = "0") entao
               escreval("Esse numero ja esta preenchido")

            senao
               jogo[l,op] <- x
               codRepetido()

            fimse
         senao
            //--------------------------------------------------------------
            se( op > 3 ) e ( op < 7) entao
               L <- 2
               se (jogo[L,op-3] = "X") ou (jogo[L,op-3] = "0") entao
                  escreval("Esse numero ja esta preenchido")

               senao
                  jogo[l,op-3] <- x
                  codRepetido()
               fimse

               //--------------------------------------------------------------
            senao
               L <- 3
               se (jogo[L,op-6] = "X") ou (jogo[L,op-6] = "0") entao
                  escreval("Esse numero ja esta preenchido")

               senao
                  jogo[l,op-6] <- x
                  codRepetido()

               fimse
            fimse
         fimse

      senao
         escreval("Opcao invalida")
         leia(a)

      fimse
      limpatela
      velha()

   ate( vencedor = verdadeiro) ou ( vez = 9 )
   se ( vencedor = verdadeiro) entao
      escreval("O jogador":2, x :2 , "vencer")
   senao
      escreval("Deu velha")

   fimse
fimprocedimento

//-----------------------------------------------------------------
procedimento codRepetido()
inicio

   vencedor <- VerificarVencedor()//procedimento
   vez <- vez + 1
   se ( vencedor = falso ) entao
      se( par % 2 <> 0 ) entao //se for impar
         x <- "0"
      senao
         x <- "X"

      fimse
   fimse
   par <- par + 1

fimprocedimento

//-----------------------------------------------------------------

funcao verificarVencedor() : logico // V ou F
var
   venceu : logico



inicio

   venceu <- falso


   //horizontal

   para i <- 1 ate 3 passo 1 faca
      se ((jogo[i,1] = jogo [i,2]) e (jogo[i,2] = jogo [i,3])) entao
         venceu <- verdadeiro


      fimse
   fimpara


   //vertical

   para i <- 1  ate 3 passo 1 faca
      se ((jogo[1,i] = jogo [2,i]) e (jogo[2,i] = jogo [3,i])) entao
         venceu <- verdadeiro



      fimse
   fimpara

   // diagonal 1

   se (jogo[1,1] = jogo [2,2]) e ( jogo[2,2] = jogo[3,3]) entao
      venceu <- verdadeiro
   fimse

   //diagonal 2

   se (jogo[1,3] = jogo[2,2]) e ( jogo[2,2] = jogo [3,1]) entao
      venceu <- verdadeiro
   fimse


   retorne venceu

fimfuncao
Var

   jogo : vetor [1..3,1..3] de caracter
   i, j , cont, op : inteiro
   x : caracter // guarda tanto o X como o 0
   vencedor : logico
   vez, l : inteiro
   par : inteiro
   a : caracter
Inicio

   cont <- 0

   PreencherMatriz()
   velha()
   jogar()


Fimalgoritmo
