# SimpleCompiler
Simple Compiler accept language below
start -> prog prog_
prog -> vtype word ( words ) block
prog_ -> vtype word ( words ) block prog_ | ε
decls -> decls_
decls_ -> decl decls_ | ε
decl -> vtype words ;
words -> word words_
words_ -> , word words_ | ε
vtype -> int | char
block -> { decls slist }
slist -> stat slist_
slist_ -> stat slist_ | ε
stat -> IF cond THEN block ELSE block
| WHILE cond block | word stat_
| RETURN expr ;
stat_ -> = expr ; | ( words ) ;
cond -> expr cond_
cond_ -> > expr | == expr
expr -> term expr_
expr_ -> ε | + term
term -> fact term_
term_ -> ε | * fact
fact -> num | word
