pipeline{ 
	agent any 
	stages{ 
	
			stage("Read AppSpace properties"){ 
			steps {script {def props = readProperties  file:'C:\\Kamal\\AppSpace.properties'
	def Var1= props["Domain_${ENV}"]
	def Var2= props["AppSpace_${ENV}"]
	def Var3= props["AppNode_${ENV}"] 
	f = new File("C:\\Kamal\\Deploy.txt")
	f.append("bwadmin upload -d  "+Var1+" -path ${PROJECT_NAME} -replace -f C:/Kamal/${PROJECT_NAME}/src/${PROJECT_NAME}.application/target/${PROJECT_NAME}"+"\n")
	def AppSpaceArray= Var2.tokenize(",")
	AppSpaceArray.each{ token -> 
	f.append("bwadmin deploy -d "+Var1+" -a " + token+" -pf C:/Kamal/${PROJECT_NAME}/src/${PROJECT_NAME}.application/META-INF/default.substvar -path ${PROJECT_NAME}"+"\n")
	f.append("bwadmin start -d "+Var1+" -a " + token+" -n "+Var3+" application ${PROJECT_NAME}.application 1.0"+"\n") 
	} 
		} 
	} 
} 
} 
}