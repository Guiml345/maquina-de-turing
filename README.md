import java.util.Scanner;
public class Maquina_Turing{
    public static void main(String args[]) {

		Scanner scan = new Scanner(System.in)

		String frase_Codificada;
		String frase_Conhecida;
		String frase_Decodificada = "";
		char letra = ' ';
		int ascii = 0;
		boolean bandeira = false;

		System.out.print("Digite a frase codificada: ");
		frase_Codificada = scan.nextLine();
		int tam = frase_Codificada.length();

		System.out.print("Digite a palavra que você tem conhecimento: ");
		frase_Conhecida = scan.nextLine();
		int tam_Frase_Conhecida = frase_Conhecida.length();

		for(int add = 1; add <= 26; add++)
		{
			frase_Decodificada = "";
			for(int i = 0; i < tam ; i++)
			{

				letra = frase_Codificada.charAt(i);
				ascii = (int)letra;
				int new_ascii = ascii;

				if(ascii != 32)
			{
				new_ascii = ascii - add;
				if(ascii >= 65 && ascii <= 90)
				{
					if(new_ascii < 65)
						new_ascii = 90 - (64 - (new_ascii));

				}
				else if(ascii >= 97 && ascii <= 122)
				{
					if(new_ascii < 97)
					{
						new_ascii = 122 - ( 96 - (new_ascii)) ;
					}
				}
			}
				letra = (char)new_ascii;
				frase_Decodificada = frase_Decodificada + letra;
			}
			int Pertence = tam - tam_Frase_Conhecida;
			for(int j = 0; j <= Pertence && bandeira == false; j++)
			{
				bandeira = true;

				for(int k = 0; k < tam_Frase_Conhecida; k++){
					int l = j+k;

					if(frase_Decodificada.charAt(l) != frase_Conhecida.charAt(k))
						bandeira = false;

				}
			}
			if(bandeira)
			{
					System.out.printf("\033[32m%d posições: %s\033[m\n", add, frase_Decodificada );
					System.out.println();
					System.out.printf("Pulando %d posições você achou a frase dodificada: %s\n", add, frase_Decodificada);
					break;
			}
			else
					System.out.printf("\033[31m%d posições: %s\033[m\n", add, frase_Decodificada );
				if (add == 26){
					System.out.println();
					System.out.print("Palavra não encontrada");
				}
		}
	}
}
