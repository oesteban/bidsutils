
Contributed by Tom Nichols. See attached for BIDSto3col.sh.  From the help...

```
  Usage: BIDSto3col.sh \[options\] BidsTSV OutBase
  
  Reads BIDS events.tsv and then creates 3 column event files, one per event type, 
  using the basename OutBase.  By default, all event types are used, and the height 
  value (3rd column) is 1.0.
  
  Options
    -e EventName   Instead of all event types, only use the given event type.
    -h ColName     Instead of using 1.0, get heigh value from column ColName.
```

Here's a demo...

```
  $ BIDSto3col.sh ds001/sub-13/func/sub-13_task-balloonanalogrisktask_run-01_events.tsv /tmp/duh
  Creating '/tmp/duh_cash_demean.txt'...
  Creating '/tmp/duh_cash_fixed_real_RT.txt'...
  Creating '/tmp/duh_control_pumps_demean.txt'...
  Creating '/tmp/duh_control_pumps_fixed_real_RT.txt'...
  Creating '/tmp/duh_explode_demean.txt'...
  Creating '/tmp/duh_pumps_demean.txt'...
  Creating '/tmp/duh_pumps_fixed_real_RT.txt'...
  $ BIDSto3col.sh -e cash_demean ds001/sub-13/func/sub-13_task-balloonanalogrisktask_run-01_events.tsv /tmp/duh
  Creating '/tmp/duh_cash_deman.txt'...
  $ BIDSto3col.sh -e cash_demean -h explode_demean ds001/sub-13/func/sub-13_task-balloonanalogrisktask_run-01_events.tsv /tmp/duh
  Creating '/tmp/duh_cash_demean.txt'...
  	WARNING: Event 'cash_demean' has non-numeric heights from 'explode_demean'
```

Note that it checks for non-numeric heights (and missing event names and/or column names).
