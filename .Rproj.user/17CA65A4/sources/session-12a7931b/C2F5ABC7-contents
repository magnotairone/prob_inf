# Renderizar livro --------------------------------------------------------

quarto::quarto_render()

quarto::quarto_preview()


# Listar tarefas a fazer --------------------------------------------------

search_term <- "TODO:"
qmd_files <- list.files(path = getwd(), pattern = "\\.qmd$", recursive = FALSE)
files_with_todo <- c()
for (file_name in qmd_files) {
  
  tryCatch({
    # Ler todas as linhas do arquivo
    # Usar encoding = "UTF-8" é uma boa prática para arquivos .qmd
    # warn = FALSE suprime avisos se o arquivo não terminar com uma linha nova
    file_content <- readLines(file_name, encoding = "UTF-8", warn = FALSE)
    
    # Verificar se ALGUMA linha contém o termo de busca exato
    # fixed = TRUE é crucial para a busca exata ("literal") e não regex
    if (any(grepl(search_term, file_content, fixed = TRUE))) {
      
      # Se encontrar, adicionar o nome do arquivo à nossa lista
      files_with_todo <- c(files_with_todo, file_name)
    }
    
  }, error = function(e) {
    # Adicionar um tratamento de erro para o caso de não conseguir ler um arquivo
    cat("Erro ao tentar ler o arquivo:", file_name, "- pulando.\n")
  })
}

if (length(files_with_todo) > 0) {
  cat("--- Arquivos encontrados com '", search_term, "' ---\n", sep = "")
  cat(paste(files_with_todo, collapse = "\n"))
  cat("\n----------------------------------------\n")
} else {
  cat("--- Nenhum arquivo .qmd encontrado com '", search_term, "' ---\n", sep = "")
}
