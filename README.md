# PA3
PA3

Pseudo code for printing symbol table

public void printSymTable(Scope sc) {
		boolean flag = false;
		HashMap<String,SymbolTableEntryClassName> tempHashMap = new HashMap(sc.getHashMap());
		List<String> keyList = new ArrayList(tempHashMap.keySet());
		Collections.sort(keyList);
		
		for (String scopeName : keyList) {
			SymbolTableEntryClassName s = tempHashMap.get(scopeName);
			if(<<check if s is a class here>>) { 
				if(!flag) {
					out.print("Classes in global scope:");
					flag = true;
				}
				out.print(" "+<<CLASS NAME>>);
			}
		}
		if(flag) {
			out.print("\n");
			flag = false;
		}
		for (String scopeName : keyList) {
			SymbolTableEntryClassName s = tempHashMap.get(scopeName);
			if(<<check if s is a Var here>>) {
				if(!flag) {
					out.print("Vars in current scope:");
					flag = true;
				}
				out.print(" "+<<VAR NAME>>+":"+<<VAR TYPE>>);
			}
		}
		if(flag) {
			out.print("\n");
			flag = false;
		}
		for (String scopeName : keyList) {
			SymbolTableEntryClassName s = tempHashMap.get(scopeName);
			if(<<check if s is a Method here>>) {
				if(!flag) {
					out.print("Methods in current scope:");
					flag = true;
				}
				out.print(" "+<<METHOD NAME>>);
			}
		}
		if(flag) {
			out.print("\n");
		}
    	for (String scopeName : keyList) {
			SymbolTableEntryClassName s = tempHashMap.get(scopeName);
    		if(<check if s is a class here>) {
    			out.println("\nIn class "+<<CLASS NAME>>+" scope");
    			this.printSymTable(<<CLASS SCOPE>>);
    		} else if(<<check if s is a method here>>) {
    			out.println("In method "+<<METHOD NAME>>+" scope");
    			//print method signature here 
				  String formals; //add logic to populate formals
    			String retType; //add logic to populate return type
    			out.println("Method Signature: ("+formals+") returns "+retType);
    			this.printSymTable(<<METHOD SCOPE>>);
    		}
    	}
    }
