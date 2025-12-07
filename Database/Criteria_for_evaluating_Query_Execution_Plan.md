### select_type
- SIMPLE, PRIMARY, DERIVED는 괜찮다.
- DEPENDENT, UNCACHEABLE은 안 좋다.

<br>

### type
- system, const, eq_ref는 괜찮다.
- index, all은 안 좋다.


<br>

### extra
- Using index는 괜찮다.
- Using filesort, Using temporary는 안 좋다.
