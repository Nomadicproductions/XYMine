# GitHub Actions Workflow for Cache Reset

## Problem Solved

Your workflow was failing to initiate because there was no automated system to switch GitHub Pages deployment between branches to reset the cache. This repository now includes two workflow solutions to fix this issue.

## What Was Added

### 1. Main Workflow: `reset-cache-branch-switch.yml`

- **Triggers**: Automatically runs when you commit to `joeyaugust1-patch-3`
- **Process**: 
  1. Switches GitHub Pages to `joeyaugust1-patch-2`
  2. Waits 30 seconds for stabilization
  3. Switches back to `joeyaugust1-patch-3`
- **Method**: Uses GitHub API directly to update Pages configuration

### 2. Alternative Workflow: `reset-cache-alternative.yml`

- **Triggers**: Same as main workflow, plus manual trigger option
- **Process**: 
  1. Creates empty commit on `joeyaugust1-patch-2` to trigger fresh deployment
  2. Waits 45 seconds
  3. Creates empty commit on `joeyaugust1-patch-3` to return to normal
- **Method**: Uses GitHub CLI and empty commits to force fresh deployments

## How to Use

### Automatic (Recommended)
1. Make your code changes on `joeyaugust1-patch-3`
2. Commit and push your changes
3. The workflow will automatically run and reset the cache
4. Your changes will be live with fresh cache

### Manual Trigger
1. Go to your repository's **Actions** tab
2. Select "Reset Cache Branch Switch" or "Reset Cache Branch Switch (Alternative)"
3. Click **Run workflow**
4. Select the branch and click **Run workflow**

## Why This Works

**GitHub Pages Cache Issue**: When you deploy the same branch repeatedly, GitHub Pages may serve cached versions of your files, making it appear like your changes aren't taking effect.

**Solution**: By temporarily switching to a different branch and then back, we force GitHub Pages to:
1. Clear its cache for the original branch
2. Rebuild and serve fresh content
3. Eliminate stale cached files

## Branches Used

- **`joeyaugust1-patch-2`** (Branch 2): Temporary switch target for cache reset
- **`joeyaugust1-patch-3`** (Branch 3): Your working branch, final deployment target

## Troubleshooting

### If workflows don't appear:
1. Make sure the files are in the `main` branch or the default branch
2. Check that the YAML syntax is valid
3. Ensure GitHub Actions is enabled in repository settings

### If workflows fail:
1. Check that both branches exist and have commits
2. Verify GitHub Pages is enabled in repository Settings > Pages
3. Ensure the repository has the proper permissions for GitHub Actions
4. Check the Actions tab for detailed error messages

### If cache reset doesn't work:
1. Try the alternative workflow (it uses a different method)
2. Verify that GitHub Pages is actually switching between branches
3. Check browser developer tools to see if files are being served from cache

## Next Steps

1. **Merge this PR** to activate the workflows
2. **Test the workflow** by making a commit to `joeyaugust1-patch-3`
3. **Monitor the Actions tab** to see the workflow execution
4. **Verify cache reset** by checking that your changes appear immediately

## Files Created

- `.github/workflows/reset-cache-branch-switch.yml` - Main API-based workflow
- `.github/workflows/reset-cache-alternative.yml` - Alternative commit-based workflow  
- `.github/workflows/README.md` - Documentation for the workflow system
- `WORKFLOW_SETUP.md` - This comprehensive setup guide

Your cache reset automation is now ready to use! 🚀