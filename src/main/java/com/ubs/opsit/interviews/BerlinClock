package com.ubs.opsit.interviews;

//Importing util classes to support the conversion of Time.
import java.util.Arrays;
import java.util.Collections;

//Importing to use join method to have a single string for comparison of Berlin time
import org.apache.commons.lang.StringUtils;

/**
 * Class implementing the Berlin Clock display of digital time.
 */
public class BerlinClock implements TimeConverter {
	private static final String NEW_LINE = System.getProperty("line.separator");
	private static final String NULL_ERROR = "Time is not provided";
	private static final String INVALID_TIME_ERROR = "Invalid time provided.";
	private static final String NON_NUMERIC_TIME_ERROR = "Time values must be number.";

	// Default constructor
	public BerlinClock() {
	}

	/*
	 * This method will convert the input digital time to formated Berlin time.
	 * 
	 * @see com.ubs.opsit.interviews.TimeConverter#convertTime(java.lang.String)
	 */
	@Override
	public String convertTime(String aTime) throws IllegalArgumentException {
		if (aTime == null)
			throw new IllegalArgumentException(NULL_ERROR);
		String[] hr_min_sec = aTime.split(":", 3);
		if (hr_min_sec.length != 3)
			throw new IllegalArgumentException(INVALID_TIME_ERROR);
		int hours, minutes, seconds = 0;
		try {
			hours = Integer.parseInt(hr_min_sec[0]);
			minutes = Integer.parseInt(hr_min_sec[1]);
			seconds = Integer.parseInt(hr_min_sec[2]);
		} catch (NumberFormatException e) {
			throw new IllegalArgumentException(NON_NUMERIC_TIME_ERROR);
		}
		if (hours < 0 || hours > 23)
			throw new IllegalArgumentException("Invalid Hour value provided.");
		if (minutes < 0 || minutes > 59)
			throw new IllegalArgumentException("Invalid Minute value provided.");
		if (seconds < 0 || seconds > 59)
			throw new IllegalArgumentException("Invalid Second value provided.");
		return convertTime(hours, minutes, seconds).trim();
	}

	/**
	 * Overloaded method for conversion.
	 *
	 * @param hours
	 *            - an int representing Hours
	 * @param minutes
	 *            - an int representing Minutes
	 * @param seconds
	 *            - an int representing Seconds
	 *
	 * @return BerlinTime object created using the parameters.
	 */
	private String convertTime(int hours, int minutes, int seconds) {
		String value1 = (seconds % 2 == 0) ? "Y" : "O";
		String value2 = formattedString(hours / 5, 4, "R");
		String value3 = formattedString(hours % 5, 4, "R");
		String value4 = formattedString(minutes / 5, 11, "Y")
				.replaceAll("YYY", "YYR");
		String value5 = formattedString(minutes % 5, 4, "Y");
		return StringUtils
				.join(Arrays.asList(value1, value2, value3, value4, value5),
						NEW_LINE);
	}

	/**
	 * String formation for each line.
	 * 
	 * @param onLights
	 * @param lightsInRow
	 * @param lampType
	 * @return String format row of the clock.
	 */
	private String formattedString(int onLights, int lightsInRow, String lampType) {
		int offLights = lightsInRow - onLights;
		String on = StringUtils.join(Collections.nCopies(onLights, lampType),
				"");
		String off = StringUtils.join(Collections.nCopies(offLights, "O"), "");
		return on + off;
	}

	// Stub for testing
	public static void main(String[] args) {
		BerlinClock clock = new BerlinClock();
		System.out.println(clock.convertTime("13:17:01"));
	}

}
