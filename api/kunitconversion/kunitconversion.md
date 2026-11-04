---
title: "KUnitConversion Namespace"
description: "Convert values in different physical units."
---

# KUnitConversion Namespace

Convert values in different physical units. [More...](#details)

- **Header:** `#include <KUnitConversion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`

## Detailed Description {#details}

## Classes {#classes}

### class [Converter](kunitconversion-converter.md)

Class for converting values between units of measurement.

### class [Unit](kunitconversion-unit.md)

Class to define a unit of measurement.

### class [UnitCategory](kunitconversion-unitcategory.md)

Class to define a category of units of measurement.

### class [UpdateJob](kunitconversion-updatejob.md)

Dynamic conversion data update job.

### class [Value](kunitconversion-value.md)

Class to hold a value in a unit of measurement.

## Type Documentation {#type-documentation}

### enum KUnitConversion::CategoryId {#CategoryId-enum}

| Constant |   |
| --- | --- |
| `KUnitConversion::InvalidCategory` | `-1` |
| `KUnitConversion::LengthCategory` | `0` |
| `KUnitConversion::AreaCategory` | `1` |
| `KUnitConversion::VolumeCategory` | `2` |
| `KUnitConversion::TemperatureCategory` | `3` |
| `KUnitConversion::VelocityCategory` | `4` |
| `KUnitConversion::MassCategory` | `5` |
| `KUnitConversion::PressureCategory` | `6` |
| `KUnitConversion::EnergyCategory` | `7` |
| `KUnitConversion::CurrencyCategory` | `8` |
| `KUnitConversion::PowerCategory` | `9` |
| `KUnitConversion::TimeCategory` | `10` |
| `KUnitConversion::FuelEfficiencyCategory` | `11` |
| `KUnitConversion::DensityCategory` | `12` |
| `KUnitConversion::WeightPerAreaCategory` | `13` |
| `KUnitConversion::AccelerationCategory` | `14` |
| `KUnitConversion::AngleCategory` | `15` |
| `KUnitConversion::FrequencyCategory` | `16` |
| `KUnitConversion::ForceCategory` | `17` |
| `KUnitConversion::ThermalConductivityCategory (since Qt 5.27)` | `18` |
| `KUnitConversion::ThermalFluxCategory (since Qt 5.27)` | `19` |
| `KUnitConversion::ThermalGenerationCategory (since Qt 5.27)` | `20` |
| `KUnitConversion::VoltageCategory (since Qt 5.27)` | `21` |
| `KUnitConversion::ElectricalCurrentCategory (since Qt 5.27)` | `22` |
| `KUnitConversion::ElectricalResistanceCategory (since Qt 5.27)` | `23` |
| `KUnitConversion::PermeabilityCategory (since Qt 5.53)` | `24` |
| `KUnitConversion::BinaryDataCategory (since Qt 5.61)` | `25` |

### enum KUnitConversion::UnitId {#UnitId-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KUnitConversion::InvalidUnit` | `-1` |   |
| `KUnitConversion::NoUnit` | `0` |   |
| `KUnitConversion::Percent` | `1` |   |
| `KUnitConversion::SquareYottameter` | `1000` |   |
| `KUnitConversion::SquareZettameter` | `1001` |   |
| `KUnitConversion::SquareExameter` | `1002` |   |
| `KUnitConversion::SquarePetameter` | `1003` |   |
| `KUnitConversion::SquareTerameter` | `1004` |   |
| `KUnitConversion::SquareGigameter` | `1005` |   |
| `KUnitConversion::SquareMegameter` | `1006` |   |
| `KUnitConversion::SquareKilometer` | `1007` |   |
| `KUnitConversion::SquareHectometer` | `1008` |   |
| `KUnitConversion::SquareDecameter` | `1009` |   |
| `KUnitConversion::SquareMeter` | `1010` |   |
| `KUnitConversion::SquareDecimeter` | `1011` |   |
| `KUnitConversion::SquareCentimeter` | `1012` |   |
| `KUnitConversion::SquareMillimeter` | `1013` |   |
| `KUnitConversion::SquareMicrometer` | `1014` |   |
| `KUnitConversion::SquareNanometer` | `1015` |   |
| `KUnitConversion::SquarePicometer` | `1016` |   |
| `KUnitConversion::SquareFemtometer` | `1017` |   |
| `KUnitConversion::SquareAttometer` | `1018` |   |
| `KUnitConversion::SquareZeptometer` | `1019` |   |
| `KUnitConversion::SquareYoctometer` | `1020` |   |
| `KUnitConversion::Acre` | `1021` |   |
| `KUnitConversion::SquareFoot` | `1022` |   |
| `KUnitConversion::SquareInch` | `1023` |   |
| `KUnitConversion::SquareMile` | `1024` |   |
| `KUnitConversion::Yottameter` | `2000` |   |
| `KUnitConversion::Zettameter` | `2001` |   |
| `KUnitConversion::Exameter` | `2002` |   |
| `KUnitConversion::Petameter` | `2003` |   |
| `KUnitConversion::Terameter` | `2004` |   |
| `KUnitConversion::Gigameter` | `2005` |   |
| `KUnitConversion::Megameter` | `2006` |   |
| `KUnitConversion::Kilometer` | `2007` |   |
| `KUnitConversion::Hectometer` | `2008` |   |
| `KUnitConversion::Decameter` | `2009` |   |
| `KUnitConversion::Meter` | `2010` |   |
| `KUnitConversion::Decimeter` | `2011` |   |
| `KUnitConversion::Centimeter` | `2012` |   |
| `KUnitConversion::Millimeter` | `2013` |   |
| `KUnitConversion::Micrometer` | `2014` |   |
| `KUnitConversion::Nanometer` | `2015` |   |
| `KUnitConversion::Picometer` | `2016` |   |
| `KUnitConversion::Femtometer` | `2017` |   |
| `KUnitConversion::Attometer` | `2018` |   |
| `KUnitConversion::Zeptometer` | `2019` |   |
| `KUnitConversion::Yoctometer` | `2020` |   |
| `KUnitConversion::Inch` | `2021` |   |
| `KUnitConversion::Foot` | `2022` |   |
| `KUnitConversion::Yard` | `2023` |   |
| `KUnitConversion::Mile` | `2024` |   |
| `KUnitConversion::NauticalMile` | `2025` |   |
| `KUnitConversion::LightYear` | `2026` |   |
| `KUnitConversion::Parsec` | `2027` |   |
| `KUnitConversion::AstronomicalUnit` | `2028` |   |
| `KUnitConversion::Thou` | `2029` |   |
| `KUnitConversion::Angstrom` | `2030` |   |
| `KUnitConversion::RackUnit` | `2031` |   |
| `KUnitConversion::Link` | `2032` |   |
| `KUnitConversion::Chain` | `2033` |   |
| `KUnitConversion::Furlong` | `2034` |   |
| `KUnitConversion::Fathom` | `2035` |   |
| `KUnitConversion::RodPerchPole` | `2036` |   |
| `KUnitConversion::CubicYottameter` | `3000` |   |
| `KUnitConversion::CubicZettameter` | `3001` |   |
| `KUnitConversion::CubicExameter` | `3002` |   |
| `KUnitConversion::CubicPetameter` | `3003` |   |
| `KUnitConversion::CubicTerameter` | `3004` |   |
| `KUnitConversion::CubicGigameter` | `3005` |   |
| `KUnitConversion::CubicMegameter` | `3006` |   |
| `KUnitConversion::CubicKilometer` | `3007` |   |
| `KUnitConversion::CubicHectometer` | `3008` |   |
| `KUnitConversion::CubicDecameter` | `3009` |   |
| `KUnitConversion::CubicMeter` | `3010` |   |
| `KUnitConversion::CubicDecimeter` | `3011` |   |
| `KUnitConversion::CubicCentimeter` | `3012` |   |
| `KUnitConversion::CubicMillimeter` | `3013` |   |
| `KUnitConversion::CubicMicrometer` | `3014` |   |
| `KUnitConversion::CubicNanometer` | `3015` |   |
| `KUnitConversion::CubicPicometer` | `3016` |   |
| `KUnitConversion::CubicFemtometer` | `3017` |   |
| `KUnitConversion::CubicAttometer` | `3018` |   |
| `KUnitConversion::CubicZeptometer` | `3019` |   |
| `KUnitConversion::CubicYoctometer` | `3020` |   |
| `KUnitConversion::Yottaliter` | `3021` |   |
| `KUnitConversion::Zettaliter` | `3022` |   |
| `KUnitConversion::Exaliter` | `3023` |   |
| `KUnitConversion::Petaliter` | `3024` |   |
| `KUnitConversion::Teraliter` | `3025` |   |
| `KUnitConversion::Gigaliter` | `3026` |   |
| `KUnitConversion::Megaliter` | `3027` |   |
| `KUnitConversion::Kiloliter` | `3028` |   |
| `KUnitConversion::Hectoliter` | `3029` |   |
| `KUnitConversion::Decaliter` | `3030` |   |
| `KUnitConversion::Liter` | `3031` |   |
| `KUnitConversion::Deciliter` | `3032` |   |
| `KUnitConversion::Centiliter` | `3033` |   |
| `KUnitConversion::Milliliter` | `3034` |   |
| `KUnitConversion::Microliter` | `3035` |   |
| `KUnitConversion::Nanoliter` | `3036` |   |
| `KUnitConversion::Picoliter` | `3037` |   |
| `KUnitConversion::Femtoliter` | `3038` |   |
| `KUnitConversion::Attoliter` | `3039` |   |
| `KUnitConversion::Zeptoliter` | `3040` |   |
| `KUnitConversion::Yoctoliter` | `3041` |   |
| `KUnitConversion::CubicFoot` | `3042` |   |
| `KUnitConversion::CubicInch` | `3043` |   |
| `KUnitConversion::CubicMile` | `3044` |   |
| `KUnitConversion::FluidOunce` | `3045` |   |
| `KUnitConversion::Cup` | `3046` |   |
| `KUnitConversion::Teaspoon` | `3047` |   |
| `KUnitConversion::Tablespoon` | `3048` |   |
| `KUnitConversion::GallonUS` | `3049` |   |
| `KUnitConversion::PintImperial` | `3050` |   |
| `KUnitConversion::OilBarrel (since Qt 5.53)` | `3051` |   |
| `KUnitConversion::GallonImperial (since Qt 5.70)` | `3052` |   |
| `KUnitConversion::PintUS (since Qt 5.70)` | `3053` |   |
| `KUnitConversion::Yottagram` | `4000` |   |
| `KUnitConversion::Zettagram` | `4001` |   |
| `KUnitConversion::Exagram` | `4002` |   |
| `KUnitConversion::Petagram` | `4003` |   |
| `KUnitConversion::Teragram` | `4004` |   |
| `KUnitConversion::Gigagram` | `4005` |   |
| `KUnitConversion::Megagram` | `4006` |   |
| `KUnitConversion::Kilogram` | `4007` |   |
| `KUnitConversion::Hectogram` | `4008` |   |
| `KUnitConversion::Decagram` | `4009` |   |
| `KUnitConversion::Gram` | `4010` |   |
| `KUnitConversion::Decigram` | `4011` |   |
| `KUnitConversion::Centigram` | `4012` |   |
| `KUnitConversion::Milligram` | `4013` |   |
| `KUnitConversion::Microgram` | `4014` |   |
| `KUnitConversion::Nanogram` | `4015` |   |
| `KUnitConversion::Picogram` | `4016` |   |
| `KUnitConversion::Femtogram` | `4017` |   |
| `KUnitConversion::Attogram` | `4018` |   |
| `KUnitConversion::Zeptogram` | `4019` |   |
| `KUnitConversion::Yoctogram` | `4020` |   |
| `KUnitConversion::Ton` | `4021` |   |
| `KUnitConversion::Carat` | `4022` |   |
| `KUnitConversion::Pound` | `4023` |   |
| `KUnitConversion::Ounce` | `4024` |   |
| `KUnitConversion::TroyOunce` | `4025` |   |
| `KUnitConversion::MassNewton` | `4026` |   |
| `KUnitConversion::Kilonewton` | `4027` |   |
| `KUnitConversion::Stone (since Qt 5.26)` | `4028` |   |
| `KUnitConversion::Yottapascal` | `5000` |   |
| `KUnitConversion::Zettapascal` | `5001` |   |
| `KUnitConversion::Exapascal` | `5002` |   |
| `KUnitConversion::Petapascal` | `5003` |   |
| `KUnitConversion::Terapascal` | `5004` |   |
| `KUnitConversion::Gigapascal` | `5005` |   |
| `KUnitConversion::Megapascal` | `5006` |   |
| `KUnitConversion::Kilopascal` | `5007` |   |
| `KUnitConversion::Hectopascal` | `5008` |   |
| `KUnitConversion::Decapascal` | `5009` |   |
| `KUnitConversion::Pascal` | `5010` |   |
| `KUnitConversion::Decipascal` | `5011` |   |
| `KUnitConversion::Centipascal` | `5012` |   |
| `KUnitConversion::Millipascal` | `5013` |   |
| `KUnitConversion::Micropascal` | `5014` |   |
| `KUnitConversion::Nanopascal` | `5015` |   |
| `KUnitConversion::Picopascal` | `5016` |   |
| `KUnitConversion::Femtopascal` | `5017` |   |
| `KUnitConversion::Attopascal` | `5018` |   |
| `KUnitConversion::Zeptopascal` | `5019` |   |
| `KUnitConversion::Yoctopascal` | `5020` |   |
| `KUnitConversion::Bar` | `5021` |   |
| `KUnitConversion::Millibar` | `5022` |   |
| `KUnitConversion::Decibar` | `5023` |   |
| `KUnitConversion::Torr` | `5024` |   |
| `KUnitConversion::TechnicalAtmosphere` | `5025` |   |
| `KUnitConversion::Atmosphere` | `5026` |   |
| `KUnitConversion::PoundForcePerSquareInch` | `5027` |   |
| `KUnitConversion::InchesOfMercury` | `5028` |   |
| `KUnitConversion::MillimetersOfMercury` | `5029` |   |
| `KUnitConversion::Kelvin` | `6000` |   |
| `KUnitConversion::Celsius` | `6001` |   |
| `KUnitConversion::Fahrenheit` | `6002` |   |
| `KUnitConversion::Rankine` | `6003` |   |
| `KUnitConversion::Delisle` | `6004` |   |
| `KUnitConversion::TemperatureNewton` | `6005` |   |
| `KUnitConversion::Reaumur` | `6006` |   |
| `KUnitConversion::Romer` | `6007` |   |
| `KUnitConversion::Yottajoule` | `7000` |   |
| `KUnitConversion::Zettajoule` | `7001` |   |
| `KUnitConversion::Exajoule` | `7002` |   |
| `KUnitConversion::Petajoule` | `7003` |   |
| `KUnitConversion::Terajoule` | `7004` |   |
| `KUnitConversion::Gigajoule` | `7005` |   |
| `KUnitConversion::Megajoule` | `7006` |   |
| `KUnitConversion::Kilojoule` | `7007` |   |
| `KUnitConversion::Hectojoule` | `7008` |   |
| `KUnitConversion::Decajoule` | `7009` |   |
| `KUnitConversion::Joule` | `7010` |   |
| `KUnitConversion::Decijoule` | `7011` |   |
| `KUnitConversion::Centijoule` | `7012` |   |
| `KUnitConversion::Millijoule` | `7013` |   |
| `KUnitConversion::Microjoule` | `7014` |   |
| `KUnitConversion::Nanojoule` | `7015` |   |
| `KUnitConversion::Picojoule` | `7016` |   |
| `KUnitConversion::Femtojoule` | `7017` |   |
| `KUnitConversion::Attojoule` | `7018` |   |
| `KUnitConversion::Zeptojoule` | `7019` |   |
| `KUnitConversion::Yoctojoule` | `7020` |   |
| `KUnitConversion::GuidelineDailyAmount` | `7021` |   |
| `KUnitConversion::Electronvolt` | `7022` |   |
| `KUnitConversion::Rydberg` | `7023` |   |
| `KUnitConversion::Kilocalorie` | `7024` |   |
| `KUnitConversion::PhotonWavelength` | `7025` |   |
| `KUnitConversion::KiloJoulePerMole` | `7026` |   |
| `KUnitConversion::JoulePerMole` | `7027` |   |
| `KUnitConversion::Btu (since Qt 5.27)` | `7028` |   |
| `KUnitConversion::Erg (since Qt 5.27)` | `7029` |   |
| `KUnitConversion::TeraWattHour (since Qt 6.28)` | `7030` | , |
| `KUnitConversion::GigaWattHour (since Qt 6.28)` | `7031` | , |
| `KUnitConversion::MegawattHour (since Qt 6.28)` | ? |   |
| `KUnitConversion::KilowattHour (since Qt 6.28)` | ? |   |
| `KUnitConversion::WattHour (since Qt 6.28)` | `7034` |   |
| `KUnitConversion::Eur` | `8000` |   |
| `KUnitConversion::Ats` | `8001` |   |
| `KUnitConversion::Bef` | `8002` |   |
| `KUnitConversion::Nlg` | `8003` |   |
| `KUnitConversion::Fim` | `8004` |   |
| `KUnitConversion::Frf` | `8005` |   |
| `KUnitConversion::Dem` | `8006` |   |
| `KUnitConversion::Iep` | `8007` |   |
| `KUnitConversion::Itl` | `8008` |   |
| `KUnitConversion::Luf` | `8009` |   |
| `KUnitConversion::Pte` | `8010` |   |
| `KUnitConversion::Esp` | `8011` |   |
| `KUnitConversion::Grd` | `8012` |   |
| `KUnitConversion::Sit` | `8013` |   |
| `KUnitConversion::Cyp` | `8014` |   |
| `KUnitConversion::Mtl` | `8015` |   |
| `KUnitConversion::Skk` | `8016` |   |
| `KUnitConversion::Usd` | `8017` |   |
| `KUnitConversion::Jpy` | `8018` |   |
| `KUnitConversion::Bgn` | `8019` |   |
| `KUnitConversion::Czk` | `8020` |   |
| `KUnitConversion::Dkk` | `8021` |   |
| `KUnitConversion::Eek` | `8022` |   |
| `KUnitConversion::Gbp` | `8023` |   |
| `KUnitConversion::Huf` | `8024` |   |
| `KUnitConversion::Ltl` | `8025` |   |
| `KUnitConversion::Lvl` | `8026` |   |
| `KUnitConversion::Pln` | `8027` |   |
| `KUnitConversion::Ron` | `8028` |   |
| `KUnitConversion::Sek` | `8029` |   |
| `KUnitConversion::Chf` | `8030` |   |
| `KUnitConversion::Nok` | `8031` |   |
| `KUnitConversion::Hrk` | `8032` |   |
| `KUnitConversion::Rub` | `8033` |   |
| `KUnitConversion::Try` | `8034` |   |
| `KUnitConversion::Aud` | `8035` |   |
| `KUnitConversion::Brl` | `8036` |   |
| `KUnitConversion::Cad` | `8037` |   |
| `KUnitConversion::Cny` | `8038` |   |
| `KUnitConversion::Hkd` | `8039` |   |
| `KUnitConversion::Idr` | `8040` |   |
| `KUnitConversion::Inr` | `8041` |   |
| `KUnitConversion::Krw` | `8042` |   |
| `KUnitConversion::Mxn` | `8043` |   |
| `KUnitConversion::Myr` | `8044` |   |
| `KUnitConversion::Nzd` | `8045` |   |
| `KUnitConversion::Php` | `8046` |   |
| `KUnitConversion::Sgd` | `8047` |   |
| `KUnitConversion::Thb` | `8048` |   |
| `KUnitConversion::Zar` | `8049` |   |
| `KUnitConversion::Ils` | `8050` |   |
| `KUnitConversion::Isk` | `8051` |   |
| `KUnitConversion::MeterPerSecond` | `9000` |   |
| `KUnitConversion::KilometerPerHour` | `9001` |   |
| `KUnitConversion::MilePerHour` | `9002` |   |
| `KUnitConversion::FootPerSecond` | `9003` |   |
| `KUnitConversion::InchPerSecond` | `9004` |   |
| `KUnitConversion::Knot` | `9005` |   |
| `KUnitConversion::Mach` | `9006` |   |
| `KUnitConversion::SpeedOfLight` | `9007` |   |
| `KUnitConversion::Beaufort` | `9008` |   |
| `KUnitConversion::Yottawatt` | `10000` |   |
| `KUnitConversion::Zettawatt` | `10001` |   |
| `KUnitConversion::Exawatt` | `10002` |   |
| `KUnitConversion::Petawatt` | `10003` |   |
| `KUnitConversion::Terawatt` | `10004` |   |
| `KUnitConversion::Gigawatt` | `10005` |   |
| `KUnitConversion::Megawatt` | `10006` |   |
| `KUnitConversion::Kilowatt` | `10007` |   |
| `KUnitConversion::Hectowatt` | `10008` |   |
| `KUnitConversion::Decawatt` | `10009` |   |
| `KUnitConversion::Watt` | `10010` |   |
| `KUnitConversion::Deciwatt` | `10011` |   |
| `KUnitConversion::Centiwatt` | `10012` |   |
| `KUnitConversion::Milliwatt` | `10013` |   |
| `KUnitConversion::Microwatt` | `10014` |   |
| `KUnitConversion::Nanowatt` | `10015` |   |
| `KUnitConversion::Picowatt` | `10016` |   |
| `KUnitConversion::Femtowatt` | `10017` |   |
| `KUnitConversion::Attowatt` | `10018` |   |
| `KUnitConversion::Zeptowatt` | `10019` |   |
| `KUnitConversion::Yoctowatt` | `10020` |   |
| `KUnitConversion::Horsepower` | `10021` |   |
| `KUnitConversion::DecibelKilowatt (since Qt 5.62)` | `10022` |   |
| `KUnitConversion::DecibelWatt (since Qt 5.62)` | `10023` |   |
| `KUnitConversion::DecibelMilliwatt (since Qt 5.62)` | `10024` |   |
| `KUnitConversion::DecibelMicrowatt (since Qt 5.62)` | `10025` |   |
| `KUnitConversion::Yottasecond` | `11000` |   |
| `KUnitConversion::Zettasecond` | `11001` |   |
| `KUnitConversion::Exasecond` | `11002` |   |
| `KUnitConversion::Petasecond` | `11003` |   |
| `KUnitConversion::Terasecond` | `11004` |   |
| `KUnitConversion::Gigasecond` | `11005` |   |
| `KUnitConversion::Megasecond` | `11006` |   |
| `KUnitConversion::Kilosecond` | `11007` |   |
| `KUnitConversion::Hectosecond` | `11008` |   |
| `KUnitConversion::Decasecond` | `11009` |   |
| `KUnitConversion::Second` | `11010` |   |
| `KUnitConversion::Decisecond` | `11011` |   |
| `KUnitConversion::Centisecond` | `11012` |   |
| `KUnitConversion::Millisecond` | `11013` |   |
| `KUnitConversion::Microsecond` | `11014` |   |
| `KUnitConversion::Nanosecond` | `11015` |   |
| `KUnitConversion::Picosecond` | `11016` |   |
| `KUnitConversion::Femtosecond` | `11017` |   |
| `KUnitConversion::Attosecond` | `11018` |   |
| `KUnitConversion::Zeptosecond` | `11019` |   |
| `KUnitConversion::Yoctosecond` | `11020` |   |
| `KUnitConversion::Minute` | `11021` |   |
| `KUnitConversion::Hour` | `11022` |   |
| `KUnitConversion::Day` | `11023` |   |
| `KUnitConversion::Week` | `11024` |   |
| `KUnitConversion::JulianYear` | `11025` |   |
| `KUnitConversion::LeapYear` | `11026` |   |
| `KUnitConversion::Year` | `11027` |   |
| `KUnitConversion::LitersPer100Kilometers` | `12000` |   |
| `KUnitConversion::MilePerUsGallon` | `12001` |   |
| `KUnitConversion::MilePerImperialGallon` | `12002` |   |
| `KUnitConversion::KilometrePerLitre` | `12003` |   |
| `KUnitConversion::YottakilogramsPerCubicMeter` | `13000` |   |
| `KUnitConversion::ZettakilogramPerCubicMeter` | `13001` |   |
| `KUnitConversion::ExakilogramPerCubicMeter` | `13002` |   |
| `KUnitConversion::PetakilogramPerCubicMeter` | `13003` |   |
| `KUnitConversion::TerakilogramPerCubicMeter` | `13004` |   |
| `KUnitConversion::GigakilogramPerCubicMeter` | `13005` |   |
| `KUnitConversion::MegakilogramPerCubicMeter` | `13006` |   |
| `KUnitConversion::KilokilogramPerCubicMeter` | `13007` |   |
| `KUnitConversion::HectokilogramsPerCubicMeter` | `13008` |   |
| `KUnitConversion::DecakilogramsPerCubicMeter` | `13009` |   |
| `KUnitConversion::KilogramsPerCubicMeter` | `13010` |   |
| `KUnitConversion::DecikilogramsPerCubicMeter` | `13011` |   |
| `KUnitConversion::CentikilogramsPerCubicMeter` | `13012` |   |
| `KUnitConversion::MillikilogramsPerCubicMeter` | `13013` |   |
| `KUnitConversion::MicrokilogramsPerCubicMeter` | `13014` |   |
| `KUnitConversion::NanokilogramsPerCubicMeter` | `13015` |   |
| `KUnitConversion::PicokilogramsPerCubicMeter` | `13016` |   |
| `KUnitConversion::FemtokilogramsPerCubicMeter` | `13017` |   |
| `KUnitConversion::AttokilogramsPerCubicMeter` | `13018` |   |
| `KUnitConversion::ZeptokilogramsPerCubicMeter` | `13019` |   |
| `KUnitConversion::YoctokilogramsPerCubicMeter` | `13020` |   |
| `KUnitConversion::KilogramPerLiter` | `13021` |   |
| `KUnitConversion::GramPerLiter` | `13022` |   |
| `KUnitConversion::GramPerMilliliter` | `13023` |   |
| `KUnitConversion::OuncePerCubicInch` | `13024` |   |
| `KUnitConversion::OuncePerCubicFoot` | `13025` |   |
| `KUnitConversion::OuncePerCubicYard` | `13026` |   |
| `KUnitConversion::PoundPerCubicInch` | `13027` |   |
| `KUnitConversion::PoundPerCubicFoot` | `13028` |   |
| `KUnitConversion::PoundPerCubicYard` | `13029` |   |
| `KUnitConversion::GramsPerSquareMeter` | `13030` |   |
| `KUnitConversion::OuncesPerSquareYard` | `13031` |   |
| `KUnitConversion::Momme (since Qt 6.25)` | `13032` |   |
| `KUnitConversion::MetresPerSecondSquared` | `14000` |   |
| `KUnitConversion::FeetPerSecondSquared` | `14001` |   |
| `KUnitConversion::StandardGravity` | `14002` |   |
| `KUnitConversion::Yottanewton` | `15000` |   |
| `KUnitConversion::Zettanewton` | `15001` |   |
| `KUnitConversion::Exanewton` | `15002` |   |
| `KUnitConversion::Petanewton` | `15003` |   |
| `KUnitConversion::Teranewton` | `15004` |   |
| `KUnitConversion::Giganewton` | `15005` |   |
| `KUnitConversion::Meganewton` | `15006` |   |
| `KUnitConversion::KilonewtonForce` | `15007` |   |
| `KUnitConversion::Hectonewton` | `15008` |   |
| `KUnitConversion::Decanewton` | `15009` |   |
| `KUnitConversion::Newton` | `15010` |   |
| `KUnitConversion::Decinewton` | `15011` |   |
| `KUnitConversion::Centinewton` | `15012` |   |
| `KUnitConversion::Millinewton` | `15013` |   |
| `KUnitConversion::Micronewton` | `15014` |   |
| `KUnitConversion::Nanonewton` | `15015` |   |
| `KUnitConversion::Piconewton` | `15016` |   |
| `KUnitConversion::Femtonewton` | `15017` |   |
| `KUnitConversion::Attonewton` | `15018` |   |
| `KUnitConversion::Zeptonewton` | `15019` |   |
| `KUnitConversion::Yoctonewton` | `15020` |   |
| `KUnitConversion::Dyne` | `15021` |   |
| `KUnitConversion::Kilopond` | `15022` |   |
| `KUnitConversion::PoundForce` | `15023` |   |
| `KUnitConversion::Poundal` | `15024` |   |
| `KUnitConversion::Degree` | `16000` |   |
| `KUnitConversion::Radian` | `16001` |   |
| `KUnitConversion::Gradian` | `16002` |   |
| `KUnitConversion::ArcMinute` | `16003` |   |
| `KUnitConversion::ArcSecond` | `16004` |   |
| `KUnitConversion::Yottahertz` | `17000` |   |
| `KUnitConversion::Zettahertz` | `17001` |   |
| `KUnitConversion::Exahertz` | `17002` |   |
| `KUnitConversion::Petahertz` | `17003` |   |
| `KUnitConversion::Terahertz` | `17004` |   |
| `KUnitConversion::Gigahertz` | `17005` |   |
| `KUnitConversion::Megahertz` | `17006` |   |
| `KUnitConversion::Kilohertz` | `17007` |   |
| `KUnitConversion::Hectohertz` | `17008` |   |
| `KUnitConversion::Decahertz` | `17009` |   |
| `KUnitConversion::Hertz` | `17010` |   |
| `KUnitConversion::Decihertz` | `17011` |   |
| `KUnitConversion::Centihertz` | `17012` |   |
| `KUnitConversion::Millihertz` | `17013` |   |
| `KUnitConversion::Microhertz` | `17014` |   |
| `KUnitConversion::Nanohertz` | `17015` |   |
| `KUnitConversion::Picohertz` | `17016` |   |
| `KUnitConversion::Femtohertz` | `17017` |   |
| `KUnitConversion::Attohertz` | `17018` |   |
| `KUnitConversion::Zeptohertz` | `17019` |   |
| `KUnitConversion::Yoctohertz` | `17020` |   |
| `KUnitConversion::RPM` | `17021` |   |
| `KUnitConversion::WattPerMeterKelvin (since Qt 5.27)` | `18000` |   |
| `KUnitConversion::BtuPerFootHourFahrenheit (since Qt 5.27)` | `18001` |   |
| `KUnitConversion::BtuPerSquareFootHourFahrenheitPerInch (since Qt 5.27)` | `18002` |   |
| `KUnitConversion::WattPerSquareMeter (since Qt 5.27)` | `19000` |   |
| `KUnitConversion::BtuPerHourPerSquareFoot (since Qt 5.27)` | `19001` |   |
| `KUnitConversion::WattPerCubicMeter (since Qt 5.27)` | `20000` |   |
| `KUnitConversion::BtuPerHourPerCubicFoot (since Qt 5.27)` | `20001` |   |
| `KUnitConversion::Yottavolts (since Qt 5.27)` | `30000` |   |
| `KUnitConversion::Zettavolts (since Qt 5.27)` | `30001` |   |
| `KUnitConversion::Exavolts (since Qt 5.27)` | `30002` |   |
| `KUnitConversion::Petavolts (since Qt 5.27)` | `30003` |   |
| `KUnitConversion::Teravolts (since Qt 5.27)` | `30004` |   |
| `KUnitConversion::Gigavolts (since Qt 5.27)` | `30005` |   |
| `KUnitConversion::Megavolts (since Qt 5.27)` | `30006` |   |
| `KUnitConversion::Kilovolts (since Qt 5.27)` | `30007` |   |
| `KUnitConversion::Hectovolts (since Qt 5.27)` | `30008` |   |
| `KUnitConversion::Decavolts (since Qt 5.27)` | `30009` |   |
| `KUnitConversion::Volts (since Qt 5.27)` | `30010` |   |
| `KUnitConversion::Decivolts (since Qt 5.27)` | `30011` |   |
| `KUnitConversion::Centivolts (since Qt 5.27)` | `30012` |   |
| `KUnitConversion::Millivolts (since Qt 5.27)` | `30013` |   |
| `KUnitConversion::Microvolts (since Qt 5.27)` | `30014` |   |
| `KUnitConversion::Nanovolts (since Qt 5.27)` | `30015` |   |
| `KUnitConversion::Picovolts (since Qt 5.27)` | `30016` |   |
| `KUnitConversion::Femtovolts (since Qt 5.27)` | `30017` |   |
| `KUnitConversion::Attovolts (since Qt 5.27)` | `30018` |   |
| `KUnitConversion::Zeptovolts (since Qt 5.27)` | `30019` |   |
| `KUnitConversion::Yoctovolts (since Qt 5.27)` | `30020` |   |
| `KUnitConversion::Statvolts (since Qt 5.27)` | `30021` |   |
| `KUnitConversion::Yottaampere (since Qt 5.27)` | `31000` |   |
| `KUnitConversion::Zettaampere (since Qt 5.27)` | `31001` |   |
| `KUnitConversion::Exaampere (since Qt 5.27)` | `31002` |   |
| `KUnitConversion::Petaampere (since Qt 5.27)` | `31003` |   |
| `KUnitConversion::Teraampere (since Qt 5.27)` | `31004` |   |
| `KUnitConversion::Gigaampere (since Qt 5.27)` | `31005` |   |
| `KUnitConversion::Megaampere (since Qt 5.27)` | `31006` |   |
| `KUnitConversion::Kiloampere (since Qt 5.27)` | `31007` |   |
| `KUnitConversion::Hectoampere (since Qt 5.27)` | `31008` |   |
| `KUnitConversion::Decaampere (since Qt 5.27)` | `31009` |   |
| `KUnitConversion::Ampere (since Qt 5.27)` | `31010` |   |
| `KUnitConversion::Deciampere (since Qt 5.27)` | `31011` |   |
| `KUnitConversion::Centiampere (since Qt 5.27)` | `31012` |   |
| `KUnitConversion::Milliampere (since Qt 5.27)` | `31013` |   |
| `KUnitConversion::Microampere (since Qt 5.27)` | `31014` |   |
| `KUnitConversion::Nanoampere (since Qt 5.27)` | `31015` |   |
| `KUnitConversion::Picoampere (since Qt 5.27)` | `31016` |   |
| `KUnitConversion::Femtoampere (since Qt 5.27)` | `31017` |   |
| `KUnitConversion::Attoampere (since Qt 5.27)` | `31018` |   |
| `KUnitConversion::Zeptoampere (since Qt 5.27)` | `31019` |   |
| `KUnitConversion::Yoctoampere (since Qt 5.27)` | `31020` |   |
| `KUnitConversion::Yottaohms (since Qt 5.27)` | `32000` |   |
| `KUnitConversion::Zettaohms (since Qt 5.27)` | `32001` |   |
| `KUnitConversion::Exaohms (since Qt 5.27)` | `32002` |   |
| `KUnitConversion::Petaohms (since Qt 5.27)` | `32003` |   |
| `KUnitConversion::Teraohms (since Qt 5.27)` | `32004` |   |
| `KUnitConversion::Gigaohms (since Qt 5.27)` | `32005` |   |
| `KUnitConversion::Megaohms (since Qt 5.27)` | `32006` |   |
| `KUnitConversion::Kiloohms (since Qt 5.27)` | `32007` |   |
| `KUnitConversion::Hectoohms (since Qt 5.27)` | `32008` |   |
| `KUnitConversion::Decaohms (since Qt 5.27)` | `32009` |   |
| `KUnitConversion::Ohms (since Qt 5.27)` | `32010` |   |
| `KUnitConversion::Deciohms (since Qt 5.27)` | `32011` |   |
| `KUnitConversion::Centiohms (since Qt 5.27)` | `32012` |   |
| `KUnitConversion::Milliohms (since Qt 5.27)` | `32013` |   |
| `KUnitConversion::Microohms (since Qt 5.27)` | `32014` |   |
| `KUnitConversion::Nanoohms (since Qt 5.27)` | `32015` |   |
| `KUnitConversion::Picoohms (since Qt 5.27)` | `32016` |   |
| `KUnitConversion::Femtoohms (since Qt 5.27)` | `32017` |   |
| `KUnitConversion::Attoohms (since Qt 5.27)` | `32018` |   |
| `KUnitConversion::Zeptoohms (since Qt 5.27)` | `32019` |   |
| `KUnitConversion::Yoctoohms (since Qt 5.27)` | `32020` |   |
| `KUnitConversion::Darcy (since Qt 5.53)` | `33000` |   |
| `KUnitConversion::MiliDarcy (since Qt 5.53)` | `33001` |   |
| `KUnitConversion::PermeabilitySquareMicrometer (since Qt 5.53)` | `33002` |   |
| `KUnitConversion::Yobibyte (since Qt 5.61)` | `34000` |   |
| `KUnitConversion::Yobibit (since Qt 5.61)` | `34001` |   |
| `KUnitConversion::Yottabyte (since Qt 5.61)` | `34002` |   |
| `KUnitConversion::Yottabit (since Qt 5.61)` | `34003` |   |
| `KUnitConversion::Zebibyte (since Qt 5.61)` | `34004` |   |
| `KUnitConversion::Zebibit (since Qt 5.61)` | `34005` |   |
| `KUnitConversion::Zettabyte (since Qt 5.61)` | `34006` |   |
| `KUnitConversion::Zettabit (since Qt 5.61)` | `34007` |   |
| `KUnitConversion::Exbibyte (since Qt 5.61)` | `34008` |   |
| `KUnitConversion::Exbibit (since Qt 5.61)` | `34009` |   |
| `KUnitConversion::Exabyte (since Qt 5.61)` | `34010` |   |
| `KUnitConversion::Exabit (since Qt 5.61)` | `34011` |   |
| `KUnitConversion::Pebibyte (since Qt 5.61)` | `34012` |   |
| `KUnitConversion::Pebibit (since Qt 5.61)` | `34013` |   |
| `KUnitConversion::Petabyte (since Qt 5.61)` | `34014` |   |
| `KUnitConversion::Petabit (since Qt 5.61)` | `34015` |   |
| `KUnitConversion::Tebibyte (since Qt 5.61)` | `34016` |   |
| `KUnitConversion::Tebibit (since Qt 5.61)` | `34017` |   |
| `KUnitConversion::Terabyte (since Qt 5.61)` | `34018` |   |
| `KUnitConversion::Terabit (since Qt 5.61)` | `34019` |   |
| `KUnitConversion::Gibibyte (since Qt 5.61)` | `34020` |   |
| `KUnitConversion::Gibibit (since Qt 5.61)` | `34021` |   |
| `KUnitConversion::Gigabyte (since Qt 5.61)` | `34022` |   |
| `KUnitConversion::Gigabit (since Qt 5.61)` | `34023` |   |
| `KUnitConversion::Mebibyte (since Qt 5.61)` | `34024` |   |
| `KUnitConversion::Mebibit (since Qt 5.61)` | `34025` |   |
| `KUnitConversion::Megabyte (since Qt 5.61)` | `34026` |   |
| `KUnitConversion::Megabit (since Qt 5.61)` | `34027` |   |
| `KUnitConversion::Kibibyte (since Qt 5.61)` | `34028` |   |
| `KUnitConversion::Kibibit (since Qt 5.61)` | `34029` |   |
| `KUnitConversion::Kilobyte (since Qt 5.61)` | `34030` |   |
| `KUnitConversion::Kilobit (since Qt 5.61)` | `34031` |   |
| `KUnitConversion::Byte (since Qt 5.61)` | `34032` |   |
| `KUnitConversion::Bit (since Qt 5.61)` | `34033` |   |
