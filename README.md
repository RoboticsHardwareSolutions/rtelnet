# telnet

Example:


```c
int __io_putchar(int ch)
{
    uint8_t ch8 = ch & 0xFF;
    TelnetWrite(ch8);
    return ch;
}
```


For freeRTOS task
```c
int __io_putchar(int ch)
{
  MX_LWIP_Init();

    if (InitializeTelnetServer() == TELNET_OK)
    {
        // error
    }
    if (TelnetIsConnected() == 1)
        { 
        /* We have an active Telnet connection to service */
        /* Do server stuff */
            char ucData = TelnetRead();
            if (ucData != '\0')
            {
                QUEUE_IN(cli_rx_buff, ucData);
                if(strstr(cli_rx_buff, "help")
                {
                    printf("help information");
                }    
            }
        }
        osDelay(1);
    }
}
```
