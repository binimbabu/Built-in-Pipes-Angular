Pipes

Pipes transform the way data is displayed on the screen. How to transform values in template

Built-in pipes

DatePipe: Formats a date value according to locale rules.


Pre-defined format options 
Option	Equivalent to	Examples (given in en-US locale)
'short'	'M/d/yy, h:mm a'	6/15/15, 9:03 AM
'medium'	'MMM d, y, h:mm:ss a'	Jun 15, 2015, 9:03:01 AM
'long'	'MMMM d, y, h:mm:ss a z'	June 15, 2015 at 9:03:01 AM GMT+1
'full'	'EEEE, MMMM d, y, h:mm:ss a zzzz'	Monday, June 15, 2015 at 9:03:01 AM GMT+01:00
'shortDate'	'M/d/yy'	6/15/15
'mediumDate'	'MMM d, y'	Jun 15, 2015
'longDate'	'MMMM d, y'	June 15, 2015
'fullDate'	'EEEE, MMMM d, y'	Monday, June 15, 2015
'shortTime'	'h:mm a'	9:03 AM
'mediumTime'	'h:mm:ss a'	9:03:01 AM
'longTime'	'h:mm:ss a z'	9:03:01 AM GMT+1
'fullTime'	'h:mm:ss a zzzz'	9:03:01 AM GMT+01:00


UpperCasePipe: transforms text to all upper case.
LowerCasePipe: transforms text to all lower case.
CurrencyPipe: Transforms a number to currency string, formatted according to locale rules.

syntax

{{ value_expression | currency:currencyCode:display:digitsInfo:locale }}

eg:-

@Component({
  selector: 'currency-pipe',
  template: `<div>
    <!--output '$0.26'-->
    <p>A: {{ a | currency }}</p>
    <!--output 'CA$0.26'-->
    <p>A: {{ a | currency: 'CAD' }}</p>
    <!--output 'CAD0.26'-->
    <p>A: {{ a | currency: 'CAD' : 'code' }}</p>
    <!--output 'CA$0,001.35'-->
    <p>B: {{ b | currency: 'CAD' : 'symbol' : '4.2-2' }}</p>
    <!--output '$0,001.35'-->
    <p>B: {{ b | currency: 'CAD' : 'symbol-narrow' : '4.2-2' }}</p>
    <!--output '0 001,35 CA$'-->
    <p>B: {{ b | currency: 'CAD' : 'symbol' : '4.2-2' : 'fr' }}</p>
    <!--output 'CLP1' because CLP has no cents-->
    <p>B: {{ b | currency: 'CLP' }}</p>
  </div>`,
  standalone: false,
})
export class CurrencyPipeComponent {
  a: number = 0.259;
  b: number = 1.3495;
}



DecimalPipe: Transforms a number into a string with a  decimal point, formatted according to locale


syntax

{{ value_expression | number:digitsInfo:locale }}

where 'digitsInfo' can be of syntax {minIntegerDigits}.{minFractionDigits}-{maxFractionDigits}

minIntegerDigits: The minimum number of integer digits before the decimal point. Default is 1.

minFractionDigits: The minimum number of digits after the decimal point. Default is 0.

maxFractionDigits: The maximum number of digits after the decimal point. Default is 3.







PercentPipe: Transforms a number to a percentage string, formatted according to locale rules.
AsyncPipe: Subscribe and unsubscribe to an asynchronous source such as an observable.
The async pipe subscribes to an Observable or Promise and returns the latest value it has emitted. When a new value is emitted, the async pipe marks the component to be checked for changes. When the component gets destroyed, the async pipe unsubscribes automatically to avoid potential memory leaks. When the reference of the expression changes, the async pipe automatically unsubscribes from the old Observable or Promise and subscribes to the new one.
eg:-

@Component({
  selector: 'async-observable-pipe',
  template: '<div> Time: {{ time | async }}</div>',
  standalone: false,
})
export class AsyncObservablePipeComponent {
  time = new Observable<string>((observer: Observer<string>) => {
    setInterval(() => observer.next(new Date().toString()), 1000);
  });
}

JsonPipe: Display a component object property to the screen as JSON for debugging.

eg:- of date pipe

{{dateObj | date :"full"}}

Output

Wednesday, July 2, 2025 at 11:29:55 AM GMT+05:30

here dateObj is the value we need to apply date pipe , '|' is the pipe symbol and 'date' is the name of pipe to be used. 'full' is arguments passed to pipe.
