# FM-Test

FM-Test is a set of tools for automated testing of FileMaker solutions. Influences include:

- The [Test Anything Protocol][1] (TAP)
- Perl's [Test::More][2] framework

[1]: http://testanything.org/
[2]: http://search.cpan.org/~mschwern/Test-Simple-0.98/lib/Test/More.pm

## Custom Functions

Custom functions are included as separate files in the Functions folder. The functions let you accumulate a log of test results in a FileMaker script. For example:

	Set Variable [$ignoreMe; Value:TestPlan ( 3 )	// plan to run 1 test]
	Set Variable [$ignoreMe; Value:TestOK ( True ; "Test is tautologically OK" )]
	Set Variable [$ignoreMe; Value:TestDiagnostic ( "This is a comment line" )]
	Set Variable [$ignoreMe; Value:TestEqual ( 1 + 1 ; 3 ; "Arithmetic: 1 + 1 = 3" )]
	Set Variable [$ignoreMe; Value:TestSkip ( 1 ; "Demonstrating TestSkip function" )]
	Set Variable [$ignoreMe; Value:TestOK ( False ; "Test with skip directive doesn't count" )]
	Exit Script [Result:TestLog]

This test will exit with this result:

	TAP version 13
	1..3
	ok 1 Test is tautologically OK
	# This is a comment line
	not ok 2 Arithmetic: 1 + 1 = 3
		---
		actual:	2
		expected:	3
		...
	not ok 3 Test with skip directive doesn't count # SKIP Demonstrating TestSkip function

Visit the [TAP website][1] for details about the log protocol, and read the header comments for each function to learn more about what it does.

## License

Anyone may do anything with this software. There is no warranty.