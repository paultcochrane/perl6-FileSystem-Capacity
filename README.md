FileSystem::Capacity::VolumesInfo
=================================

Provides filesystem capacity info in bytes or human format from operating system utils and tools.

Currently implements:
* GNU/Linux filesystem by df command from coreutils.
* Win32 filesystem by wmic command.
* OS X filesystem by df command.

## Installing the module ##

    panda update
    panda --notests install FileSystem::Capacity::VolumesInfo

    (I will resolve the travis test stuff to avoid --notests)

## Example Usage ##
    use v6;
    use FileSystem::Capacity::VolumesInfo;

    say "Byte version:\n";

    my %vols = volumes-info();

    for %vols.sort(*.key)>>.kv -> ($location, $data) {
      say "Location: $location";
      say "Size: $data<size> bytes";
      say "Used: $data<used> bytes";
      say "Used%: $data<used%>";
      say "Free: $data<free> bytes";
      say "---";
    }

    say "----";

    say "Human version:\n";

    my %vols-human = volumes-info(:human);

    for %vols-human.sort(*.key)>>.kv -> ($location, $data) {
      say "Location: $location";
      say "Size: $data<size>";
      say "Used: $data<used>";
      say "Used%: $data<used%>";
      say "Free: $data<free>";
      say "---";
    }
