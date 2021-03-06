
```graphql
{
  data:queryStatus(from:"100", to:"5000", sourceId:"default") {
    fxStatus {
      packet {
        inverterCurrentRaw
        outputVoltageRaw
        inverterWattage
        warningModes
        address
        miscModes
        batteryVoltage
        acMode
        acModeName
        packetType
      }
    }
  }
}
```

```graphql
{
  data:queryEventIdentifier(from:"$__from", to:"$__to", sourceId:"default", fragmentId:1, identifier:"SupplementaryIdentifier(identifier=OutbackIdentifier(address=2), supplementaryType=FX_OPERATIONAL_MODE_CHANGE)") {
    fxOperationalModeChange {
      Time:dateMillis
      packet {
        operationalModeValue
      }
    }
  }
}
```


This query is used for displaying the operating mode in a table. You can make `packet.identifier.representation` 'hidden'.
```graphql
{
  data:queryStatusLast(to:"$timeTo", sourceId:"default", reversed:true) {
    fxStatus {
      Time:dateMillis
      packet {
        identityInfo { displayName }
        operatingModeName
        identifier { representation }
      }
    }
  }
}
```

This is used in the battery voltage gauge. The `Time` is important.
```graphql
{
  data:queryStatusLast(to:"$timeTo", sourceId:"default") {
    batteryVoltage {
      Time:dateMillis
      packet {
        batteryVoltage
      }
    }
  }
}
```
