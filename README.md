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
gh workflow view windows-vnt.yml --yaml --repo liugenglong/win-rdp
gh workflow list --repo liugenglong/win-rdp

gh api user/repos --jq '.[]' #整个仓库的详情（数组）
gh api user/repos --jq '.[].full_name' #整个仓库中所有项目全名

# 根目录（与 .github 并列的那一层）
gh api repos/liugenglong/win-rdp/contents --jq '.[] | "\(.type)  \(.name)"'
# .github 下的全部条目
gh api repos/liugenglong/win-rdp/contents/.github --jq '.[] | "\(.type)  \(.name)"'
# 整个仓库的完整目录树（递归，一次到底）
gh api repos/liugenglong/win-rdp/git/trees/main?recursive=1 --jq '.tree[] | "\(.type)  \(.path)"'

##############
PS C:\Users\Administrator> gh api repos/liugenglong/win-rdp/contents --jq '.[] | "\(.type)  \(.name)"'
dir  .github
file  README.md
PS C:\Users\Administrator> gh api repos/liugenglong/win-rdp/contents/.github --jq '.[] | "\(.type)  \(.name)"'
dir  workflows
PS C:\Users\Administrator> gh api repos/liugenglong/win-rdp/git/trees/main?recursive=1 --jq '.tree[] | "\(.type)  \(.path)"'
tree  .github
tree  .github/workflows
blob  .github/workflows/windows-desktop.yml
blob  .github/workflows/windows-vnt.yml
blob  README.md
##############

gh api repos/liugenglong/win-rdp #单个项目全部详情
gh api repos/liugenglong/win-rdp/contents/.github/workflows --jq '.[].name'
gh repo view liugenglong/win-rdp #单个项目全部详情

gh repo view liugenglong/win-rdp --web(-w) #直接网页查看
