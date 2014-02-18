#include <stdio.h>
#include <mysql/mysql.h>

char data[20], hora[20], abertura[20], fechamento[20], alta[20], baixa[20], volume[20];

void ler_arquivo();
void status_conexao();


int main(){
	leitura_arquivo();
	status_conexao();
} 

void status_conexao(){

      MYSQL conexao;

      mysql_init(&conexao);

      if ( mysql_real_connect(&conexao, "localhost", "root", "cleitoncsg", "basededados", 0, NULL, 0) ){ 
            printf("conectado com sucesso!\n");
	    mysql_query(&conexao,"INSERT INTO historico(data, hora, abertura, fechamento, alta, baixa, volume) values( '"data"', '"hora"',      '"abertura"','"fechamento"', '"alta"', '"baixa"','"volume"');");
            mysql_close(&conexao);
      }
      else{
            printf("Falha de conexao\n");
            printf("Erro %d : %c\n", mysql_errno(&conexao), mysql_error(&conexao));
       }
}

void leitura_arquivo(){
	FILE *arquivo;
	
	arquivo = fopen("banco.txt", "rt");
	fscanf(arquivo, "%s %s %s %s %s %s %s",  data, hora, abertura, baixa, alta, fechamento, volume);
	printf("%s %s %s %s %s %s %s\n", data, hora, abertura, baixa, alta, fechamento, volume);

	printf("Dados lidos do arquivo com sucesso!\n");
}







