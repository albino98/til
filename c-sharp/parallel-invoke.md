# C# Parallel Invoke

~~~
protected override void OnStart(string[] args)
        {
            
            Parallel.Invoke(() =>
            {
                _Logger.Info(nameof(OnStart), DateTime.Now.ToString("dd/MM/yyyy HH:mm:ss") + "  *********** Avvio primo task ***********\n\n");
                connection();
                notifications();
            },
            () =>
            {
                _Logger.Info(nameof(OnStart), DateTime.Now.ToString("dd/MM/yyyy HH:mm:ss") + "  *********** Avvio secondo task ***********\n\n");
                SetUpTimer(new TimeSpan(Int32.Parse(oraTimerPeb), Int32.Parse(minTimerPeb), 00));
            }
            );
            
            _Logger.DebugOut(nameof(OnStart), "");
        }
~~~
