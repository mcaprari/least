LIBDIR=`erl -eval 'io:format("~s~n", [code:lib_dir()])' -s init stop -noshell`
APP_NAME="fermal"
VSN="pre 0.1"
.PHONY = compile
all: compile

docs:
	erl -noshell -run edoc_run application "'$(APP_NAME)'" '"."' '$(VSN)' -s init stop

compile: src/least_yecc.erl src/least_lex.erl
	@mkdir -p ebin
	
	@erl -make

src/least_yecc.erl:
	erl -eval "yecc:yecc('src/least','src/least_yecc')." -noshell -s init stop
	
src/least_lex.erl:
	erl -eval "leex:file('src/least_lex')" -noshell -s init stop
		
clean:
	rm -f ebin/*.beam
	rm -f erl_crash.dump
