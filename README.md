# Sorting station

Elabore um projeto que selecione os materiais da esteira com base na sua cor (RGB)

O algoritmo elaborad segue uma lógica semelhante à seguinte:

```VB
DB
    SensorReading 
    OnRoute
    IsRaw
    IsBase 
    IsLid
    RawCnt
    BaseCnt
    LidCnt

StartButton
    ExitConveyor
    MOVE FALSE TO DB.OnRoute
NOT DB.OnRoute
    EntryConveyor
    NOT StopBlade
MOVE VisionSensor TO DB.SensorReading
DB.SensorReading == 1 OR 
DB.SensorReading == 4
    MOVE TRUE  TO DB.IsRaw
    MOVE FALSE TO DB.IsBase
    MOVE FALSE TO DB.IsLid
DB.SensorReading == 2 OR 
DB.SensorReading == 5
    MOVE FALSE TO DB.IsRaw
    MOVE TRUE  TO DB.IsBase
    MOVE FALSE TO DB.IsLid
DB.SensorReading == 3 OR 
DB.SensorReading == 6
    MOVE FALSE TO DB.IsRaw
    MOVE FALSE TO DB.IsBase
    MOVE TRUE  TO DB.IsLid
MOVE TRUE TO DB.OnRoute
DB.IsRaw
    Sort1Turn
    Sort1Belt
    ADD 1 TO DB.RawCnt
DB.IsBase
    Sort2Turn
    Sort2Belt
    ADD 1 TO DB.BaseCnt
DB.IsLid
    Sort3Turn
    Sort3Belt
    ADD 1 TO DB.LidCnt
AtExit
    MOVE FALSE TO DB.OnRoute

```