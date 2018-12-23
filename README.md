# SimpleCompiler
Simple Compiler accept language below<br>
start -> prog prog_<br>
prog -> vtype word ( words ) block<br>
prog_ -> vtype word ( words ) block prog_ | ε<br>
decls -> decls_<br>
decls_ -> decl decls_ | εv
decl -> vtype words ;<br>
words -> word words_<br>
words_ -> , word words_ | ε<br>
vtype -> int | char<br>
block -> { decls slist }<br>
slist -> stat slist_<br>
slist_ -> stat slist_ | ε<br>
stat -> IF cond THEN block ELSE block<br>
| WHILE cond block | word stat_<br>
| RETURN expr ;<br>
stat_ -> = expr ; | ( words ) ;<br>
cond -> expr cond_<br>
cond_ -> > expr | == expr<br>
expr -> term expr_<br>
expr_ -> ε | + term<br>
term -> fact term_<br>
term_ -> ε | * fact<br>
fact -> num | word<br>
