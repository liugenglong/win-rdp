gh run list --workflow="windows-desktop.yml" --repo liugenglong/win-rdp
gh run view 34428013999 --repo liugenglong/win-rdp --verbose
gh run cancel 34428013999 --repo liugenglong/win-rdp
gh workflow run windows-desktop.yml --repo liugenglong/win-rdp
gh run view 34426571955 --log --repo liugenglong/win-rdp | findstr RDPIP
gh run view (gh run list --repo liugenglong/win-rdp --limit 1 --json databaseId -q '.[0].databaseId') --log --repo liugenglong/win-rdp | findstr RDPIP
gh run view 34435861419 --repo liugenglong/win-rdp --json status,conclusion
{
  "conclusion": "cancelled",
  "status": "completed"
}
gh run watch 34435861419 --repo liugenglong/win-rdp
gh run delete 34339052616 --repo liugenglong/win-rdp
