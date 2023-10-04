# BDimport java.util.Scanner;
import java.util.Random;

public class MontyHall {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        System.out.println("Bem-vindo ao Jogo do Monty Hall!");
        System.out.println("Escolha uma porta (1, 2 ou 3):");
        int escolhaDoUsuario = scanner.nextInt();

        // Gera uma porta com um carro aleatoriamente
        int portaComCarro = random.nextInt(3) + 1;

        // Monty escolhe uma porta com um bode
        int portaComBode = 0;
        while (portaComBode == 0 || portaComBode == escolhaDoUsuario || portaComBode == portaComCarro) {
            portaComBode = random.nextInt(3) + 1;
        }

        System.out.println("Eu abri a porta " + portaComBode + ", e há um bode lá dentro.");

        System.out.println("Você quer trocar de porta? (Digite 'sim' ou 'nao')");
        String trocarPorta = scanner.next();

        boolean trocar = trocarPorta.equalsIgnoreCase("sim");

        if (trocar) {
            // Troca a porta escolhida pelo usuário
            escolhaDoUsuario = 6 - escolhaDoUsuario - portaComBode;
        }

        if (escolhaDoUsuario == portaComCarro) {
            System.out.println("Parabéns! Você ganhou um carro!");
        } else {
            System.out.println("Infelizmente, você ganhou um bode.");
        }
    }
}
