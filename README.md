# SimpleCompiler
Simple Compiler accept language below


```
    start -> prog prog_
    prog -> vtype word ( words ) block
    prog_ -> vtype word ( words ) block prog_ | ε
    decls -> decls_
    decls_ -> decl decls_ | εv
    decl -> vtype words ;
    words -> word words_
    words_ -> , word words_ | ε
    vtype -> int | char<br>
    block -> { decls slist }<br>
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
    fact -> num | word<

```
## Arguments
```
./compiler2018 soruce 
```

- source : path for source code to compile

## Documentation
[document](https://github.com/beatheat/SimpleCompiler/blob/master/COMPILER_PROJECT.pdf)

## Examples

Source
```
int funcA(a, b)
{
	int c;
	c = a + b;
}
int funcM(a, b)
{
	int c;
	c = a * b;	
}
int main(args)
{
	int a, b, c, d;
	a = 1;
	b = 2;
	c = 3;
	d = a + b * c; 
	funcA(a, b);
	funcM(a, b);
}
```

Assembly Code Generated
```
	LD	Reg#0, 1
	ST	Reg#0, a
	LD	Reg#0, 2
	ST	Reg#0, b
	LD	Reg#0, 3
	ST	Reg#0, c
	LD	Reg#0, a
	LD	Reg#1, b
	LD	Reg#2, c
	MUL	Reg#1, Reg#1, Reg#2
	ADD	Reg#0, Reg#0, Reg#1
	ST	Reg#0, d
	LD	A_Reg#0, a
	LD	A_Reg#1, b
	CALL	funcA, label0
	LD	A_Reg#0, a
	LD	A_Reg#1, b
	CALL	funcM, label1
	END

label0::	LD	Reg#0, a
	LD	Reg#1, b
	ADD	Reg#0, Reg#0, Reg#1
	ST	Reg#0, c
	JUMP	Return_Adress

label1::	LD	Reg#0, a
	LD	Reg#1, b
	MUL	Reg#0, Reg#0, Reg#1
	ST	Reg#0, c
	JUMP	Return_Adress


Number of using Registers : 5
[Reg: 3 // AReg: 2]
```