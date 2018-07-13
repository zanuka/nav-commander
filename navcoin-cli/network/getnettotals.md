# getnettotals

Returns information about network traffic, including bytes in, bytes out,
and current time.

## Result:
    {
      "totalbytesrecv": n,   (numeric) Total bytes received
      "totalbytessent": n,   (numeric) Total bytes sent
      "timemillis": t,       (numeric) Total cpu time
      "uploadtarget":
      {
        "timeframe": n,                         (numeric) Length of the measuring timeframe in seconds
        "target": n,                            (numeric) Target in bytes
        "target_reached": true|false,           (boolean) True if target is reached
        "serve_historical_blocks": true|false,  (boolean) True if serving historical blocks
        "bytes_left_in_cycle": t,               (numeric) Bytes left in current time cycle
        "time_left_in_cycle": t                 (numeric) Seconds left in current time cycle
      }
    }

## Examples:
    > navcoin-cli getnettotals