# accesslogfile
package readfile;

import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class accesslog {
	private String timestamp ;
	private String threadid ;
	private String classname;
	private String logmessage;

	String getTimeStamp (){
		return this.timestamp;
	}

	void setTimeStamp(String timestamp){
		this.timestamp=timestamp;
	}

	String getThreadID (){
		return this.threadid;
	}
	void setThreadID(String threadid){
		this.threadid=threadid;
	}
	String getClassName (){
		return this.classname;
	}
	void setClassName(String classname){
		this.classname=classname;
	}
	String getLogMessage (){
		return this.logmessage;
	}
	void setLogmessage(String logmessage){
		this.logmessage=logmessage;
	}
	public static void main(String args[]) {
		accesslog s= new accesslog();
		Scanner in = null;
		boolean isFileFound = false;
		try {
			in = new Scanner(new File("./sample.log"));
			isFileFound=true;
		} catch (FileNotFoundException e) {
			System.out.println("The file with name sample.log is not found");
		}
		if (isFileFound == true){
			while (in.hasNext()) 
			{
				String line = in.nextLine();

				String timestampstring = line.substring(1, 25);
				s.setTimeStamp(timestampstring);

				String threadidstring = line.substring(27,35);
				s.setThreadID(threadidstring);

				String classnamestring = line.substring(36,98);
				s.setClassName(classnamestring);

				String Logmessagestring = line.substring(99);
				s.setLogmessage(Logmessagestring);

				System.out.println("Timestamp = " +s.getTimeStamp());
				System.out.println("Thread ID = " +s.getThreadID() );
				System.out.println("ClassName = " +s.getClassName() );
				System.out.println("LogMessage = " + s.getLogMessage());

				System.out.println();
				System.out.println();
			}
		}





	}
}
