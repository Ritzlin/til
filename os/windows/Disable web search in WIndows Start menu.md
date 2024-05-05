# Disable web search in Windows Start menu

Web search in Windows Start menu may slow down the search.

Disable it by following steps:

1. Open Registry Editor to `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Search`.
2. Create a new `DWORD (32-bit) Value` named `BingSearchEnabled`.
3. Set the value to `0`.
4. Restart Windows Explorer or restart the computer.

From:

- [Speed up your Start Menu by disabling Web Search](https://weblog.west-wind.com/posts/2024/May/03/Speed-up-your-Start-Menu-by-disabling-Web-Search)