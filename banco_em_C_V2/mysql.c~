#include <stdio.h>
#include <mysql/mysql.h>

char data[20], hora[20], abertura[20], fechamento[20], alta[20], baixa[20], volume[20];

void leitura_arquivo();
void status_conexao();

int main(){
	leitura_arquivo();
	status_conexao();
} 

void status_conexao(){

      MYSQL conexao;
      int registro_inserido;
      char *query[100];

      mysql_init(&conexao);

      if ( mysql_real_connect(&conexao, "localhost", "root", "cleitoncsg", "basededados", 0, NULL, 0) ){ 
            printf("conectado ao banco com sucesso!\n");

	    sprintf(query,"INSERT INTO historico (data, hora, abertura, fechamento, alta, baixa, volume) values                                ('%s', '%s','%s','%s','%s','%s','%s');", data, hora, abertura, fechamento, alta, baixa, volume);
            registro_inserido = mysql_query(&conexao,query);

	    if (!registro_inserido) 
                 printf("Quantidade de registros inseridos %d\n", mysql_affected_rows(&conexao));
            mysql_close(&conexao);
	    
       }
       else{
            printf("Falha de conexao\n");
            printf("Erro %d : %s\n", mysql_errno(&conexao), mysql_error(&conexao));
       }
}
void leitura_arquivo(){
	FILE *arquivo;
	
	arquivo = fopen("banco.txt", "rt");
	fscanf(arquivo, "%s %s %s %s %s %s %s",  data, hora, abertura, baixa, alta, fechamento, volume);
	//printf("%s %s %s %s %s %s %s\n", data, hora, abertura, baixa, alta, fechamento, volume);

	printf("Dados lidos do arquivo com sucesso!\n");
}







