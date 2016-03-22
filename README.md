/**
 * A program to carry on conversations with a human user.
 * This is the initial version that:  
 * <ul><li>
 *       Uses indexOf to find strings
 * </li><li>
 * 		    Handles responding to simple words and phrases 
 * </li></ul>
 * This version uses a nested if to handle default responses.
 * @author Laurie White
 * @version April 2012
 */
public class Magpie
{
	/**
	 * Get a default greeting 	
	 * @return a greeting
	 */
	private int questionNumber=0;
	boolean isNameGiven=false;
	boolean isNameRegistered=false;
	String name="";
	public String getGreeting()
	{
		return "Hello, let's talk.";
	}
	
	/**
	 * Gives a response to a user statement
	 * 
	 * @param statement
	 *            the user statement
	 * @return a response based on the rules given
	 */
	public String getResponse(String statement)
	{
		String response = "";
		String UCstatement=statement.toUpperCase();
		if(isNameGiven==true && isNameRegistered==false)
		{
			name=statement;
			response = "So your name is "+name+". Got it.";
			isNameRegistered=true;
		}
		else if (UCstatement.indexOf("NO") >= 0)
		{
			response = "Why so negative?";
		}
		else if (UCstatement.indexOf("MOTHER") >= 0
				|| UCstatement.indexOf("FATHER") >= 0
				|| UCstatement.indexOf("SISTER") >= 0
				|| UCstatement.indexOf("BROTHER") >= 0)
		{
			response = "Tell me more about your family.";
		}
		else if(statement.trim().compareTo("")==0)
		{
			response = "Say something please";
		}
		else if(UCstatement.indexOf("PAPER")>=0)
		{
			PlayRPS("P");
		}
		else if(UCstatement.indexOf("ROCK")>=0)
		{
			PlayRPS("R");
		}
		else if(UCstatement.indexOf("SCISSORS")>=0){PlayRPS("S");}else if(UCstatement.indexOf("NAME")>=0){if(isNameGiven==false){isNameGiven=true;response = "What is your name?";}else{response="Your name is "+name;}}else if(UCstatement.substring(UCstatement.length()-1).indexOf("?")>=0){if(questionNumber%3==0){response="When you ask me 100 questions, I'll say something special.";questionNumber++;}else{response="I don't answer questions made by you humans";questionNumber++;}if(questionNumber%100==0){response="You took the time to ask 100 questions? You have no life.";}}else if(UCstatement.indexOf("BACKWARDS")>=0 || UCstatement.indexOf("REVERSE")>=0){String output="";String input= getRandomResponse();String inputP=input.substring(input.length()-1);input=input.substring(0,input.length()-1);while(input.length()>0){output=output+input.substring(input.length()-1);input=input.substring(0,input.length()-1);}response=output+inputP;}else if(UCstatement.indexOf("GAME")>=0){response="I dont play games";}else{response = getRandomResponse();}return response;}private String getRandomResponse(){final int NUMBER_OF_RESPONSES = 4;double r = Math.random();int whichResponse = (int)(r * NUMBER_OF_RESPONSES);String response = "";if (whichResponse == 0){response = "Interesting, tell me more.";}else if (whichResponse == 1){response = "Hmmm.";}else if (whichResponse == 2){response = "Do you really think so?";}else if (whichResponse == 3){response = "You don't say.";}return response;}public void PlayRPS(String userPlay){String computerPlay="";String personPlay=userPlay;int computerInt=(int)(Math.random()*2);  if(computerInt==0){computerPlay="R";System.out.println("I played Rock");}else if(computerInt==1){computerPlay="S";System.out.println("I played Scissors");}else if(computerInt==2){computerPlay="P";System.out.println("I played Paper");}else if(computerInt<0 || computerInt>2)System.out.println("Number out of bounds");if(personPlay.compareTo(computerPlay)==-3){System.out.println("My scissors cut apart your paper!" + " \nPRO TIP: Paper is not a very good weapon.");}else if(personPlay.compareTo(computerPlay)==-2){System.out.println("Your paper covered my rock!\nBut then my rock shredded apart your flimsy paper defense!");}else if(personPlay.compareTo(computerPlay)==-1){System.out.println("Your rock smashes my scissors!\nBut you're the one playing Rock Paper Scissors with a computer so who is the real loser here.");}else if(personPlay.compareTo(computerPlay)==0){System.out.println("This game was a tie.\nYou thought I would say something here. You thought wrong.");}else if(personPlay.compareTo(computerPlay)==1){System.out.println("My rock smashes your scissors!" + " \nMy rock smashes EVERYTHING.");}else if(personPlay.compareTo(computerPlay)==2){System.out.println("My paper covers your rock!" + " \nMy paper is made out of steel and contains the Rock!");}else if(personPlay.compareTo(computerPlay)==3){System.out.println("Your scissors cuts my paper!\nIts Super Effective!");}else{System.out.println("Whatever you played, I cut apart with an energy sword!");}}}
